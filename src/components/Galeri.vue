<script setup>
import { ref } from "vue";
const props = defineProps({ data: Object });
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
        <div>
          <h2 class="text-center text-primary text-2xl mb-5">Moment Kami</h2>

          <Splide
            :options="{
              type: 'loop',
              perPage: 1,
              autoplay: true,
              interval: 2000,
              pagination: true,
              arrows: false,
              gap: 10,
              pauseOnHover: false,
            }"
            class="mb-5"
          >
            <SplideSlide v-for="item in props.data?.galeri" :key="item">
              <img
                :src="item"
                alt="Amantrana"
                class="w-full h-[40dvh] object-cover"
              />
            </SplideSlide>
          </Splide>

          <Splide
            :options="{
              type: 'loop',
              perPage: 3,
              autoplay: true,
              interval: 2000,
              pagination: false,
              arrows: false,
              gap: 10,
              pauseOnHover: false,
            }"
            class=""
          >
            <SplideSlide v-for="item in props.data?.galeri" :key="item">
              <img
                :src="item"
                alt="Amantrana"
                class="w-full h-[150px] object-cover"
              />
            </SplideSlide>
          </Splide>
        </div>
      </div>
    </div>
  </v-container>
</template>
