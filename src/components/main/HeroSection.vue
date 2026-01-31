<script setup lang="ts">
import ProductSwiper from '@/components/main/ProductSwiper.vue'
</script>

<template>
  <section>
    <div
      class="bg-[#fff] bg-[url('https://im8health.com/cdn/shop/files/Frame_1000004811-min.jpg?v=1727698766')] bg-no-repeat bg-center bg-[length:100%_auto] p-[32px_0_80px]!"
    >
      <div class="page-width">
        <div class="flex">
          <product-swiper />
          <div class="bg-black min-w-[630px] h-screen"></div>
        </div>
      </div>
    </div>
  </section>
</template>
