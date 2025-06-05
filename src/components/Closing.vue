<script setup>
const props = defineProps({ data: Object, caption: Object });
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
          <div
            class="text-center mb-10 px-5"
            data-aos="zoom-in"
            data-aos-delay="500"
          >
            <p
              class="text-[14px]"
              v-html="props.caption?.islam?.penutup[2]"
            ></p>
          </div>
          <div
            class="absolute bottom-[15vh] left-0 w-full"
            data-aos="fade-up"
            data-aos-delay="1000"
          >
            <div class="flex justify-center mt-[20vh]">
              <img src="/public/logo.png" alt="Āmantrana" class="w-20" />
            </div>
            <div class="text-center">
              <small>Digital Wedding Invitation © 2025</small>
            </div>
          </div>
        </div>
      </div>
    </div>
  </v-container>
</template>
