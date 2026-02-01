<template>
  <div
    :class="isShowing ? 'translate-y-0 opacity-100' : 'translate-y-40 opacity-0 invisible'"
    class="delay-1000 fixed bottom-0 transition-all duration-1000 left-0 w-full bg-[linear-gradient(135deg,rgba(245,234,234,0.95)_0%,rgba(255,255,255,0.98)_100%)] backdrop-blur-[20px] text-[#333] z-2 flex border-t border-[rgba(80,0,11,0.12)] h-[90px] justify-center ease-[cubic-bezier(0.16,1,0.3,1)] overflow-visible before:content-[''] before:absolute before:top-0 before:left-0 before:right-0 before:h-[1px] before:bg-[linear-gradient(90deg,transparent_0%,rgba(80,0,11,0.2)_50%,transparent_100%)]"
  >
    <div class="page-width flex items-center justify-between w-full overflow-visible">
      <div class="flex gap-[18px] items-center overflow-visible">
        <div
          class="will-change-auto relative rounded-[12px] overflow-hidden bg-[linear-gradient(145deg,#ffffff,#f8f8f8)] shadow-[0_4px_16px_rgba(80,0,11,0.08),0_2px_8px_rgba(0,0,0,0.04),inset_0_1px_0_rgba(255,255,255,0.8)] transition-all duration-400 ease-[cubic-bezier(0.4,0,0.2,1)] flex"
        >
          <img
            src="https://im8health.com/cdn/shop/files/PDP_060fbac6-1883-4c53-aae5-f791c68056a5.jpg?v=1766566335&amp;width=500"
            alt="Daily Ultimate Essentials: All-in-One Supplement"
            srcset="
              https://im8health.com/cdn/shop/files/PDP_060fbac6-1883-4c53-aae5-f791c68056a5.jpg?v=1766566335&amp;width=500
            "
            width="500"
            height="500"
            class="w-[90px] max-w-[90px] h-auto object-cover rounded-[8px] transition-all duration-400 ease relative z-[2]"
            id="sticky-product-image"
            style="opacity: 1"
          />
          <div class="image-glow"></div>
        </div>

        <div
          class="font-semibold text-[#50000b] text-[16px] leading-[1.3] [font-synthesis:none] [-webkit-font-smoothing:antialiased] [-moz-osx-font-smoothing:grayscale] [text-rendering:optimizeLegibility] [contain:layout]"
        >
          Daily Ultimate Essentials: All-in-One Supplement

          <div
            class="font-medium min-h-[1em] visible"
            data-title="Daily Ultimate Essentials: All-in-One Supplement"
          >
            (Forever Jar)
          </div>
        </div>
      </div>
      <div
        class="tablet:ml-auto text-[14px]! flex gap-[12px] items-center relative visible will-change-auto"
      >
        <div class="relative w-[280px] h-fit text-left [contain:none] overflow-visible">
          <!-- SELECTED -->
          <div
            @click="isOpenDropdown = !isOpenDropdown"
            class="leading-[1.3] transition-all duration-300 ease [-webkit-font-smoothing:antialiased] [-moz-osx-font-smoothing:grayscale] [text-rendering:optimizeLegibility] [contain:layout] border border-[#50000b] py-[8px] px-[30px] rounded-[20px] cursor-pointer bg-[#f9f4f4] text-[#50000b] font-bold min-h-[42px] flex flex-col justify-center"
          >
            <div
              class="[-webkit-font-smoothing:antialiased] [-moz-osx-font-smoothing:grayscale] [text-rendering:optimizeLegibility] min-h-[1.3em]"
            >
              {{ labelOptions[optionIndexSelected]?.title }}
            </div>
            <div
              class="text-[12px] text-[rgba(80,0,11,0.8)] font-medium tracking-[0.01em] [text-rendering:optimizeLegibility]"
            >
              {{ labelOptions[optionIndexSelected]?.price }}
            </div>
            <span
              :class="{
                'rotate-180': isOpenDropdown,
              }"
              class="absolute right-[20px] top-[18px] w-0 h-0 border-l-[6px] border-l-transparent border-r-[6px] border-r-transparent border-t-[6px] border-t-[#50000b] transition-transform duration-300 ease will-change-auto"
            ></span>
          </div>
          <ul
            v-if="isOpenDropdown"
            class="-top-[200%] mb-[5px] mt-0 absolute bg-white border border-[#50000b] rounded-[20px] list-none m-[5px_0_0] p-0 z-[1000] overflow-hidden w-full shadow-[0_4px_20px_rgba(0,0,0,0.15)]"
          >
            <li
              @click="
                () => {
                  optionIndexSelected = index
                  isOpenDropdown = false
                }
              "
              class="py-[10px] px-[20px] text-[16px] cursor-pointer text-[#50000b] font-bold border-b border-[#f2f2f2] last:border-b-0 hover:bg-[#f9f4f4]"
              v-for="(option, index) in options"
              :key="index"
            >
              {{ option }}
            </li>
          </ul>
          <!-- END SELECTED -->
        </div>
        <button
          class="bg-[linear-gradient(135deg,#50000b_0%,#6b0010_100%)] w-[300px] min-w-[300px] text-white py-[15px] px-[40px] rounded-[24px] font-semibold uppercase cursor-pointer border-0 h-[50px] relative overflow-hidden transition-all duration-300 ease-[cubic-bezier(0.4,0,0.2,1)] whitespace-nowrap [contain:layout] before:content-[''] before:absolute before:top-0 before:left-[-100%] before:w-full before:h-full before:bg-[linear-gradient(90deg,transparent,rgba(255,255,255,0.1),transparent)] before:transition-[left] before:duration-[600ms] before:ease font-aeonik hover:before:left-[100%] flex items-center"
        >
          <span
            class="inline relative z-[2] [-webkit-font-smoothing:antialiased] [-moz-osx-font-smoothing:grayscale] [text-rendering:optimizeLegibility] tablet:block hidden"
            >Add to cart <span class="button-text-price"> - $78.33 USD/mo</span></span
          >
          <span class="text-mobile tablet:hidden">Add</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'

const isShowing = ref(false)
const options = ['90-Day Supply', '30-Day Supply']
const optionIndexSelected = ref<number>(0)
const labelOptions = [
  {
    title: '90-Day Supply (Save 30%)',
    price: '$2.61 USD / serving',
  },
  {
    title: '30-Day Supply',
    price: '$2.97 USD / serving',
  },
]
const isOpenDropdown = ref(false)

onMounted(() => {
  isShowing.value = true
})
</script>
