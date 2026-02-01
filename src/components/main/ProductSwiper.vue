<template>
  <div class="flex mx-auto gap-6 min-h-[1px] max-h-[750px] sticky top-40">
    <div class="relative min-w-24 flex flex-col z-1">
      <button
        v-show="!isBeginning"
        @click="swiperThumbs?.slidePrev()"
        class="absolute top-0 left-1/2 -translate-x-1/2 z-10 bg-white p-1 flex justify-center w-full"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
        </svg>
      </button>

      <swiper
        direction="vertical"
        :slides-per-view="6"
        :slides-per-group="3"
        :space-between="10"
        :allow-touch-move="false"
        :no-swiping="true"
        :breakpoints="{
          1140: {
            slidesPerView: 8.2,
            spaceBetween: 0,
          },
        }"
        class="h-full w-full"
        @swiper="onThumbsSwiper"
        @slideChange="onThumbsChange"
      >
        <swiper-slide v-for="(img, idx) in images" :key="idx" class="cursor-pointer">
          <div
            @click="activeIndex = idx"
            class="rounded-2xl overflow-hidden border transition-all w-[70px] h-[80px] xl:h-[105px] xl:w-[94px]"
            :class="activeIndex === idx ? 'border-[#a40011]' : 'opacity-100 border-transparent'"
          >
            <img :src="img" class="w-full h-full object-cover" />
          </div>
        </swiper-slide>
      </swiper>

      <button
        v-show="!isEnd"
        @click="swiperThumbs?.slideNext()"
        class="absolute bottom-0 left-1/2 -translate-x-1/2 z-10 bg-white w-full p-1 hover:text-[#a40011] flex justify-center"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 9l-7 7-7-7"
          />
        </svg>
      </button>
    </div>

    <div class="flex-1 rounded-3xl bg-white flex flex-col items-center justify-start h-fit">
      <div class="w-full max-w-full">
        <transition
          enter-active-class="transition-all duration-100 delay-100 ease-out "
          enter-from-class="opacity-0 -translate-y-2"
          enter-to-class="opacity-100 translate-y-0"
          leave-active-class="transition-all duration-100 ease-in"
          leave-from-class="opacity-100"
          leave-to-class="opacity-0"
        >
          <img
            :key="activeIndex"
            :src="images[activeIndex]"
            class="w-full h-full object-contain drop-shadow-2xl rounded-3xl overflow-hidden"
          />
        </transition>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import type { Swiper as SwiperType } from 'swiper'
import 'swiper/css'

const images = [
  'https://im8health.com/cdn/shop/files/PDP_060fbac6-1883-4c53-aae5-f791c68056a5.jpg?v=1766566335&width=823',
  'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel02.jpg?v=1761040602&width=823',
  'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel03.jpg?v=1761040601&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel01.jpg?v=1761040602&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel02.jpg?v=1761042620&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel03.jpg?v=1761040602&width=823',
  'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel04.jpg?v=1761040602&width=823',
  'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel05.jpg?v=1761040601&width=823',
  'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel06.jpg?v=1761040602&width=823',
  'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel07.jpg?v=1761040602&width=823',
  'https://im8health.com/cdn/shop/files/PDP_1f993d55-9054-40cb-b0b6-36961706db9b.webp?v=1769913343&width=823',
  'https://im8health.com/cdn/shop/files/PDP_14ef8054-a625-458b-85d8-7f236bc8922a.webp?v=1769913002&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-sachet_carousel07.jpg?v=1761040602&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel04.jpg?v=1761040602&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel05.jpg?v=1761040602&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel06.jpg?v=1761040602&width=823',
  // 'https://im8health.com/cdn/shop/files/pdp_essentials-jar_carousel07.jpg?v=1761040602&width=823',
]

const activeIndex = ref(0)
const swiperThumbs = ref<SwiperType | null>(null)
const isBeginning = ref(true)
const isEnd = ref(false)

const onThumbsSwiper = (swiper: SwiperType) => {
  swiperThumbs.value = swiper
}

const onThumbsChange = (swiper: SwiperType) => {
  isBeginning.value = swiper.isBeginning
  isEnd.value = swiper.isEnd
}
</script>

<style scoped></style>
