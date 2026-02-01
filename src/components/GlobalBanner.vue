<script setup lang="ts">
import getURL from '@/utils'
</script>

<template>
  <div class="z-1 fixed w-full z-9 top-0 left-0 m-0 block">
    <div class="page-width max-w-full! px-[56px]! bg-[#50000b] border-b border-[#50000B]">
      <div
        class="flex justify-between items-center min-h-[88px] p-0! gap-0 max-w-[1400px]! mx-auto"
      >
        <div class="flex w-[calc(100%-320px)] pr-[10px] items-center">
          <a :href="getURL" style="display: flex" aria-label="Go to homepage">
            <img
              class="w-[137px] h-[35px]"
              src="//im8health.com/cdn/shop/files/Header_White_logo.png?v=1731856481"
              alt=""
              srcset="
                //im8health.com/cdn/shop/files/Header_White_logo.png?v=1731856481&amp;width=352   352w,
                //im8health.com/cdn/shop/files/Header_White_logo.png?v=1731856481&amp;width=832   832w,
                //im8health.com/cdn/shop/files/Header_White_logo.png?v=1731856481&amp;width=1200 1200w,
                //im8health.com/cdn/shop/files/Header_White_logo.png?v=1731856481&amp;width=1328 1328w
              "
              width="1328"
              height="342"
            />
          </a>
          <div class="text-white text-[18px] h-full flex-grow text-center">
            <strong>2026 STARTS NOW:</strong> 35% OFF — Feel Like Yourself Again
          </div>
        </div>
        <div class="w-[320px]">
          <a
            :href="getURL"
            class="flex items-center justify-center rounded-[100px] bg-[#a40011] py-[13px] px-[17px] min-w-[272px] text-white text-[16px] font-bold leading-[22px] tracking-[0.32px] uppercase hover:bg-[#50000b] transition-all duration-300 w-full"
            >Get Started</a
          >
        </div>
      </div>
    </div>
  </div>
</template>
