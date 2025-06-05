<script setup>
const props = defineProps({ quote: Object });
</script>
<template>
  <v-container class="h-[100dvh] p-0">
    <img
      src="/public/img/bg.jpg"
      alt="Amantrana"
      class="w-full h-full object-cover"
    />
    <div class="absolute top-0 left-0 w-full h-full px-4 pt-10 pb-20">
      <div
        class="relative bg-white/60 h-full flex w-full justify-center items-center px-8 py-5 rounded-xl"
      >
        <div class="text-center" data-aos="zoom-in" data-aos-delay="500">
          <p class="text-[14px] text-gray-800">
            {{ props.quote?.islam[2].quote }}
          </p>
          <h3 class="text-xl mt-3">
            {{ props.quote?.islam[0].sumber }}
          </h3>
        </div>
      </div>
    </div>
  </v-container>
</template>
