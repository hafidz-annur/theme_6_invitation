<script setup>
const props = defineProps({ name: String, data: Object });

const emits = defineEmits(["selected"]);
const openInvitation = () => {
  emits("selected", "Pembukaan");
};
</script>
<template>
  <v-container height="100dvh" class="relative p-0 overflow-hidden">
    <img
      src="/public/img/bg.jpg"
      class="w-full h-[100dvh] object-cover"
      alt=""
    />

    <div
      class="absolute top-0 left-0 flex w-100 h-full items-center justify-center py-10 px-8 overflow-hidden"
    >
      <div
        class="relative h-[80dvh] w-full flex justify-center items-center rounded-xl bg-white/60 text-center font-serif text-[#4b3f2f]"
      >
        <div class="px-10">
          <p class="uppercase tracking-wider text-base">The Wedding of</p>
          <h1 class="text-4xl font-bold mt-2">
            {{ props.data?.mempelai.pria.nama_panggilan }} &
            {{ props.data?.mempelai.wanita.nama_panggilan }}
          </h1>
          <div class="flex justify-center my-5">
            <img
              :src="props.data?.foto_cover[0]"
              class="w-[150px] h-[200px] rounded-full object-cover"
            />
          </div>
          <p class="mt-4">Kepada Yth. Bapak/Ibu/Saudara/i</p>
          <v-card color="brown" variant="tonal" class="mt-2">
            <v-card-text class="text-gray-700 text-sm">
              <p>
                {{ props.name || "Tamu Undangan" }}
              </p>
            </v-card-text>
          </v-card>
          <small>
            Mohon maaf apabila ada penulisan nama/gelar yang tidak sesuai.
          </small>
        </div>
      </div>
    </div>
    <div class="absolute bottom-[8dvh] left-0 w-full flex justify-center mt-5">
      <v-btn
        icon="mdi-chevron-down"
        color="green"
        class="animate__animated animate__fadeInDown animate__repeat-2"
        @click="openInvitation"
        size="small"
      />
    </div>
  </v-container>
</template>
