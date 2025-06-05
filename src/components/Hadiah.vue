<script setup>
import { ref } from "vue";

const props = defineProps({ data: Object });
const tab = ref("one");

const copyText = (text) => {
  navigator.clipboard
    .writeText(text)
    .then(() => {
      alert("Berhasil disalin", text);
    })
    .catch((err) => {
      console.error("Failed to copy text:", err);
    });
};
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
          <div class="text-center mb-3" data-aos="zoom-in" data-aos-delay="500">
            <h4 class="mb-1 text-2xl text-primary-700">Terima Kasih</h4>
            <p class="text-gray-800">
              Terima kasih telah menambah semangat kegembiraan pernikahaan kam
              dengan kehadiran dan hadiah indah Anda.
            </p>
          </div>

          <v-tabs
            v-model="tab"
            align-tabs="center"
            data-aos="zoom-in"
            data-aos-delay="1000"
            class="bg-primary"
          >
            <v-tab
              value="one"
              class="text-[12px]"
              :class="tab == 'one' ? 'bg-secondary text-gray-500' : null"
              >Bank</v-tab
            >
            <v-tab
              value="two"
              class="text-[12px]"
              :class="tab == 'two' ? 'bg-secondary text-gray-500' : null"
              >E-Wallet</v-tab
            >
            <v-tab
              value="three"
              class="text-[12px]"
              :class="tab == 'three' ? 'bg-secondary text-gray-500' : null"
              >Kirim Kado</v-tab
            >
          </v-tabs>
          <div
            class="py-3 bg-white/40 px-3"
            data-aos="zoom-in"
            data-aos-delay="1000"
          >
            <v-tabs-window v-model="tab" align-tabs="center">
              <v-tabs-window-item value="one">
                <div class="md:h-[350px] h-[260px] overflow-auto">
                  <div
                    v-for="item in props.data?.hadiah?.bank"
                    :key="item"
                    class="mb-3 bg-green-400/60 p-2 py-4 rounded-lg shadow-lg"
                  >
                    <div class="flex justify-between items-center">
                      <div class="">
                        <p class="text-center text-gray-800 my-1">
                          {{ item.atas_nama }}
                        </p>
                        <div class="flex items-center text-white mt-1">
                          <v-icon
                            icon="mdi-wallet-bifold-outline"
                            class="me-2"
                          ></v-icon>
                          {{ item.norek }}
                        </div>
                      </div>
                      <div class="w-[80px] text-right">
                        <img
                          :src="'img/bank/' + item.nama + '.png'"
                          class="mb-2"
                        />
                        <v-btn
                          color="primary"
                          prepend-icon="mdi-content-copy"
                          @click="copyText(item.norek)"
                          size="small"
                        >
                          Salin
                        </v-btn>
                      </div>
                    </div>
                  </div>
                </div>
              </v-tabs-window-item>

              <v-tabs-window-item value="two">
                <div class="md:h-[350px] h-[260px] overflow-auto">
                  <div
                    v-for="item in props.data?.hadiah?.ewallet"
                    :key="item"
                    class="mb-3 bg-green-400/60 p-2 py-4 rounded-lg shadow-lg"
                  >
                    <div class="flex justify-between items-center">
                      <div class="">
                        <p class="text-center text-gray-800 my-1">
                          {{ item.atas_nama }}
                        </p>
                        <div class="flex items-center text-white mt-1">
                          <v-icon
                            icon="mdi-wallet-bifold-outline"
                            class="me-2"
                          ></v-icon>
                          {{ item.norek }}
                        </div>
                      </div>
                      <div class="w-[80px] text-right">
                        <img
                          :src="'img/bank/' + item.nama + '.png'"
                          class="mb-2"
                        />
                        <v-btn
                          color="primary"
                          prepend-icon="mdi-content-copy"
                          @click="copyText(item.norek)"
                          size="small"
                        >
                          Salin
                        </v-btn>
                      </div>
                    </div>
                  </div>
                </div>
              </v-tabs-window-item>

              <v-tabs-window-item value="three">
                <div class="text-center">
                  <v-icon icon="mdi-gift-outline" size="40" class="mb-2" />
                  <h3 class="text-2xl">Alamat</h3>
                  <p class="mt-3 text-gray-800">
                    {{ props.data?.hadiah?.alamat }}
                  </p>
                </div>
              </v-tabs-window-item>
            </v-tabs-window>
          </div>
        </div>
      </div>
    </div>
  </v-container>
</template>
