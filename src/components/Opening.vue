<script setup>
import { ref } from "vue";
import moment from "moment";

const props = defineProps({ data: Object, caption: Object });
const deadline = ref(props.data?.acara.resepsi.raw_tanggal + "10:00:00");

const saveCalendar = () => {
  const title =
    "&text=Undangan Pernikahan " +
    props.data?.mempelai.pria.nama_panggilan +
    " - " +
    props.data?.mempelai.wanita.nama_panggilan;
  const description =
    "&details=Dalam+perjalanan+yang+penuh+rasa+dan+doa%2C%0Akami+memantapkan+hati+untuk+melangkah+bersama+dalam+ikatan+suci.%0AKami+mengundang+dengan+penuh+cinta+dan+harap%2C%0Aagar+Bapak%2FIbu%2FSaudara%2Fi+dapat+hadir%0Amerayakan+momen+bahagia+kami.";
  const location = "&location=" + props.data?.acara?.resepsi?.tempat;
  const dates =
    "&dates=" +
    moment(deadline.value).utc().format("YYYYMMDDTHHmmss[Z]") +
    "%2F" +
    moment(deadline.value).utc().format("YYYYMMDDTHHmmss[Z]");

  const url =
    "https://www.google.com/calendar/render?action=TEMPLATE" +
    title +
    description +
    location +
    dates;

  window.open(url, "_blank");
};
</script>
<template>
  <v-container height="100dvh" class="relative overflow-hidden p-0">
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
            class="text-center pt-5 animate__animated animate__zoomIn animate__delay-1s"
          >
            <p
              v-html="props.caption?.islam?.pembuka[2]"
              class="text-[12px] mt-3"
            ></p>
          </div>
          <div class="flex justify-center my-5 animate__animated animate__zoomIn animate__delay-2s">
            <img
              :src="props.data?.foto_cover[0]"
              class="w-[150px] h-[200px] rounded-full object-cover"
            />
          </div>
          <div
            class="flex justify-center animate__animated animate__zoomIn animate__delay-3s"
          >
            <div class="w-full text-center">
              <h1 class="text-4xl">
                {{ props.data?.mempelai.pria.nama_panggilan }} &
                {{ props.data?.mempelai.wanita.nama_panggilan }}
              </h1>

              <p class="mb-3">
                {{ props.data?.acara.resepsi.tanggal_format }}
              </p>

              <vue3-flip-countdown
                countdownSize="1.4rem"
                labelSize=".8rem"
                mainColor="green"
                labelColor="green"
                :flipAnimation="false"
                :labels="{
                  days: 'Hari',
                  hours: 'Jam',
                  minutes: 'Menit',
                  seconds: 'Detik',
                }"
                :deadline="props.data?.acara?.resepsi?.raw_tanggal"
                class="animate__animated animate__zoomIn animate__delay-2s text-white"
              />

              <v-btn
                color="primary"
                size="small"
                prepend-icon="mdi-calendar"
                @click="saveCalendar"
                class="mt-3"
                rounded="full"
              >
                Simpan Tanggal
              </v-btn>
            </div>
          </div>
        </div>
      </div>
    </div>
  </v-container>
</template>

<style>
.flip-clock__piece {
  margin: 0 10px !important;
}
</style>
