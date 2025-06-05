<script setup>
const props = defineProps({ data: Object });
</script>
<template>
  <v-container class="relative h-[100dvh] p-0 overflow-hidden">
    <img
      src="/public/img/bg.jpg"
      alt="Amantrana"
      class="w-full h-full object-cover"
    />
    <div class="absolute top-0 left-0 w-full h-full px-4 pt-10 pb-20">
      <div
        class="relative bg-white/60 h-full flex w-full justify-center items-center py-5 rounded-xl"
      >
        <div class="text-center w-full">
          <div
            v-html="props.data?.lokasi?.maps_embed"
            class="h-[50dvh] w-full relative overflow-hidden"
          ></div>
          <v-btn
            :href="props.data?.lokasi?.maps_link"
            target="_blank"
            class="mt-5"
            append-icon="mdi-google-maps"
            prepend-icon="mdi-google-maps"
            color="primary"
            size="small"
            rounded="full"
          >
            Lihat Lokasi
          </v-btn>
        </div>
      </div>
    </div>
  </v-container>
</template>
