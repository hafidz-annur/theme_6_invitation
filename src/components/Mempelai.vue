<script setup>
const props = defineProps({ data: Object });
</script>
<template>
  <v-container class="relative h-[100dvh] p-0">
    <img
      src="/public/img/bg.jpg"
      alt="Amantrana"
      class="w-full h-full object-cover"
    />
    <div class="absolute top-0 left-0 w-full h-full px-4 pt-10 pb-20">
      <div
        class="relative bg-white/60 h-full flex w-full justify-center items-center px-8 py-5 rounded-xl"
      >
        <div class="text-center">
          <div class="" data-aos="zoom-in" data-aos-delay="500">
            <div class="flex justify-center mb-2">
              <img
                :src="props.data?.mempelai.pria.foto"
                alt="Amantrana"
                class="w-[100px] h-[150px] rounded-t-full object-cover object-top shadow"
              />
            </div>
            <h3 class="text-2xl">
              {{ props.data?.mempelai.pria.nama_lengkap }}
            </h3>
            <p class="mb-0 text-[12px]">
              Putra
              {{ props.data?.mempelai.pria.anak_ke }} dari
            </p>
            <p class="text-[13px] mt-0">
              {{ props.data?.mempelai.pria.orang_tua?.ayah }} &
              {{ props.data?.mempelai.pria.orang_tua?.ibu }}
            </p>
            <p class="flex justify-center text-end mt-2">
              <v-icon icon="mdi-instagram" class="me-2" />
              {{ props.data?.mempelai.pria.nama_panggilan }}
            </p>
          </div>
          <h2
            class="text-2xl mt-2 mb-3 flex justify-center items-center gap-5"
            data-aos="zoom-in"
            data-aos-delay="1000"
          >
            <v-divider thickness="3" color="white" opacity="1" length="10" />
            Dengan
            <v-divider thickness="3" color="white" opacity="1" length="10" />
          </h2>
          <div class="" data-aos="zoom-in" data-aos-delay="1500">
            <div class="flex justify-center mb-2">
              <img
                :src="props.data?.mempelai.wanita.foto"
                alt="Amantrana"
                class="w-[100px] h-[150px] rounded-b-full object-cover object-top shadow"
              />
            </div>
            <h3 class="text-2xl">
              {{ props.data?.mempelai.wanita.nama_lengkap }}
            </h3>
            <p class="mb-0 text-[12px]">
              Putri
              {{ props.data?.mempelai.wanita.anak_ke }} dari
            </p>
            <p class="text-[13px] mt-0">
              {{ props.data?.mempelai.wanita.orang_tua?.ayah }} &
              {{ props.data?.mempelai.wanita.orang_tua?.ibu }}
            </p>
            <p class="flex justify-center text-end mt-2">
              <v-icon icon="mdi-instagram" class="me-2" />
              {{ props.data?.mempelai.wanita.nama_panggilan }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </v-container>
</template>
