<script setup>
import { ref, onMounted, watch } from "vue";

const props = defineProps({ data: String, active: String });
const emit = defineEmits(["selected"]);

let intervalId;
const audio = ref(null);
const autoplay_menu = ref(false);
const autoplay_music = ref(false);
const hide_menu = ref(false);
const menus = ref([
  {
    icon: "mdi-home",
    title: "Pembukaan",
  },
  {
    icon: "mdi-comment-quote-outline",
    title: "Quotes",
  },
  {
    icon: "mdi-account-heart-outline",
    title: "Mempelai",
  },
  {
    icon: "mdi-calendar-star",
    title: "Acara",
  },
  {
    icon: "mdi-map-marker-radius-outline",
    title: "Lokasi",
  },
  {
    icon: "mdi-multimedia",
    title: "Galeri",
  },
  {
    icon: "mdi-gift-open-outline",
    title: "Hadiah",
  },
  {
    icon: "mdi-send-variant-outline",
    title: "RSVP",
  },
  {
    icon: "mdi-emoticon-wink-outline",
    title: "Penutupan",
  },
]);

const selected = ref(null);
const selectedMenu = () => {
  emit("selected", selected.value);
  if (autoplay_menu.value) {
    autoplay_menu.value = false;
    clearInterval(intervalId);
  }
};

const autoplayMenu = () => {
  if (autoplay_menu.value) {
    let index = menus.value.findIndex((menu) => menu.title === selected.value);
    const menus_count = menus.value.length;

    intervalId = setInterval(() => {
      if (index >= menus_count) {
        autoplay_menu.value = false;
        selected.value = "Pembukaan";
        clearInterval(intervalId);
        emit("selected", selected.value);
        return;
      }

      const element = menus.value[index].title;
      selected.value = element;
      emit("selected", selected.value);
      index++;
    }, 5000);
  } else {
    clearInterval(intervalId);
  }
};

const playMusic = () => {
  if (!audio.value) return;

  if (audio.value.paused) {
    audio.value
      .play()
      .then(() => {
        autoplay_music.value = true;
      })
      .catch((err) => {
        console.error("Audio play failed:", err);
      });
  } else {
    audio.value.pause();
    autoplay_music.value = false;
  }
};

watch(() => {
  if (props.active) {
    selected.value = props.active;
  }
});

onMounted(() => {
  audio.value = new Audio(props.data?.musik);
  autoplay_menu.value = true;
  autoplayMenu();
  playMusic();
});
</script>

<template>
  <div
    class="fixed z-[9999] flex transition-all ease-in-out duration-500"
    :class="
      hide_menu
        ? 'bottom-5 w-full justify-center gap-2'
        : 'bottom-[60px] flex-col right-7'
    "
  >
    <v-btn
      size="x-small"
      color="primary"
      :icon="!autoplay_menu ? 'mdi-play-outline' : 'mdi-pause'"
      @click="
        autoplay_menu = !autoplay_menu;
        autoplayMenu();
      "
      class="mb-2"
    />
    <v-btn
      size="x-small"
      color="primary"
      :icon="!autoplay_music ? 'mdi-volume-off' : 'mdi-volume-high'"
      @click="playMusic()"
      class="mb-2"
    />
    <v-btn
      size="x-small"
      color="primary"
      :icon="!hide_menu ? 'mdi-chevron-down' : 'mdi-chevron-up'"
      @click="hide_menu = !hide_menu"
      class="mb-2"
    />
  </div>
  <div
    class="fixed left-[5%] w-[90%] z-[9999] transition-all ease-in-out duration-500"
    :class="hide_menu ? '-bottom-[100dvh]' : 'bottom-2'"
  >
    <v-tabs
      v-model="selected"
      align-tabs="center"
      height="50"
      stacked
      center-active
      class="bg-green-800/50 rounded-full"
      @update:model-value="selectedMenu()"
    >
      <v-tab
        density="compact"
        v-for="item in menus"
        :value="item.title"
        class="p-0"
        :class="item.title == selected ? 'bg-white text-primary' : null"
      >
        <v-icon :icon="item.icon" size="20" />
        <!-- <p
          class="text-[10px]"
          :class="item.title == selected ? 'text-primary' : null"
        >
          {{ item.title }}
        </p> -->
      </v-tab>
    </v-tabs>
  </div>
</template>
<style>
.v-tab.v-tab.v-btn {
  min-width: 10px !important;
}
</style>
