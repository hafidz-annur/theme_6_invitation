<script setup>
import moment from "moment";

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
          <div
            data-aos="zoom-in"
            data-aos-delay="500"
            class="flex justify-center mb-5"
          >
            <p class="w-[60%]">
              Bergabunglah bersama Kami menyaksikan sekaligus merayakan
              terbentuknya ikatan suci ini. Kami ingin Anda menjadi bagian dari
              hari istimewa kami.
            </p>
          </div>

          <div class="flex justify-center">
            <div class="w-[70%]">
              <div data-aos="fade-left" data-aos-delay="1000">
                <div class="p-5 py-2">
                  <v-icon
                    icon="mdi-book-heart-outline"
                    class="mb-2"
                    size="25"
                    color="primary"
                  ></v-icon>
                  <h4 class="text-2xl text-primary text-nowrap">Akad Nikah</h4>
                </div>
                <div>
                  <div
                    class="flex justify-center items-center gap-3 md:px-10 px-2"
                  >
                    <div class="w-40">
                      <v-divider thickness="3" color="primary" opacity="1" />
                      <p class="my-2 text-center">
                        {{ props.data?.acara?.akad_nikah?.hari }}
                      </p>
                      <v-divider thickness="3" color="primary" opacity="1" />
                    </div>
                    <div class="w-20">
                      <p>
                        {{ props.data?.acara?.akad_nikah?.tahun }}
                      </p>
                      <p class="text-3xl">
                        {{ props.data?.acara?.akad_nikah?.tanggal }}
                      </p>
                      <p></p>
                    </div>
                    <div class="w-40 text-center">
                      <v-divider thickness="3" color="primary" opacity="1" />
                      <p class="my-2">
                        {{ props.data?.acara?.akad_nikah?.bulan }}
                      </p>
                      <v-divider thickness="3" color="primary" opacity="1" />
                    </div>
                  </div>
                  <div class="text-center mt-4">
                    <p>
                      {{ props.data?.acara?.akad_nikah?.waktu }}
                    </p>
                    <p>
                      {{ props.data?.acara?.akad_nikah?.tempat }}
                    </p>
                  </div>
                </div>
              </div>
              <div class="flex justify-center">
                <div
                  class="w-50 flex justify-center"
                  data-aos="zoom-in"
                  data-aos-delay="1000"
                >
                  <v-divider
                    thickness="3"
                    opacity=".5"
                    color="primary"
                    class="w-50 my-4 mt-6"
                  />
                </div>
              </div>
              <div data-aos="fade-right" data-aos-delay="1000">
                <div class="p-5 py-2">
                  <v-icon
                    icon="mdi-store-marker"
                    class="mb-2"
                    size="25"
                    color="primary"
                  ></v-icon>
                  <h4 class="text-2xl text-primary text-nowrap">Resepsi</h4>
                </div>
                <div>
                  <div
                    class="flex justify-center items-center gap-3 md:px-10 px-2"
                  >
                    <div class="w-40">
                      <v-divider thickness="3" color="primary" opacity="1" />
                      <p class="my-2 text-center">
                        {{ props.data?.acara?.resepsi?.hari }}
                      </p>
                      <v-divider thickness="3" color="primary" opacity="1" />
                    </div>
                    <div class="w-20">
                      <p>
                        {{ props.data?.acara?.resepsi?.tahun }}
                      </p>
                      <p class="text-3xl">
                        {{ props.data?.acara?.resepsi?.tanggal }}
                      </p>
                    </div>
                    <div class="w-40 text-center">
                      <v-divider thickness="3" color="primary" opacity="1" />
                      <p class="my-2">
                        {{ props.data?.acara?.resepsi?.bulan }}
                      </p>
                      <v-divider thickness="3" color="primary" opacity="1" />
                    </div>
                  </div>
                  <div class="text-center mt-4">
                    <p>
                      {{ props.data?.acara?.resepsi?.waktu }}
                    </p>
                    <p>
                      {{ props.data?.acara?.resepsi?.tempat }}
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </v-container>
</template>
