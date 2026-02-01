<script setup lang="ts">
import ProductSwiper from '@/components/main/ProductSwiper.vue'
import ProductDetails from '@/components/main/ProductDetails.vue'
</script>

<template>
  <section>
    <div
      class="bg-[#fff] bg-[url('https://im8health.com/cdn/shop/files/Frame_1000004811-min.jpg?v=1727698766')] bg-no-repeat bg-top bg-[length:100%_auto] p-[32px_0_80px]!"
    >
      <div class="page-width">
        <div class="flex">
          <product-swiper />
          <product-details />
        </div>
      </div>
    </div>
  </section>
</template>
