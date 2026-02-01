<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Mousewheel, FreeMode } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/free-mode'
import { ref } from 'vue'
import ChevronDownCustom from '../icon/ChevronDownCustom.vue'
import StarCustomIcon from '../icon/StarCustomIcon.vue'
import getURL from '@/utils'
import BackdropBlur from '../popup/BackdropBlur.vue'
import SwiperVideoPopup from '../popup/SwiperVideoPopup.vue'

const modules = [Mousewheel, FreeMode]

const body = document.body
const currentFormSelectIndex = ref('selectForm1')
const currentSubscribeSelectIndex = ref('subscribeForm1')
const selectForm1 = ref<HTMLElement | null>(null)
const selectForm2 = ref<HTMLElement | null>(null)
const selectSubscribe1 = ref<HTMLElement | null>(null)
const selectSubscribe2 = ref<HTMLElement | null>(null)

const openQuestionIndex = ref<number | null>(null)
const openVideoIndex = ref<number>(0)
const openVideoSwiper = ref<boolean>(false)

const handleOpenVideoSwiper = (index: number) => {
  openVideoIndex.value = index
  openVideoSwiper.value = true
  body.style.overflow = 'hidden'
}
const toggleQuestion = (index: number) => {
  openQuestionIndex.value = openQuestionIndex.value === index ? null : index
}

const tpExperts = <{ img: string; name: string; title: string }[]>[
  {
    img: 'https://im8health.com/cdn/shop/files/sab_Dawn_grid.jpg?v=1747304298&width=300',
    name: 'Dr. Dawn Mussallem',
    title: 'Cancer Survivor & Physician at Mayo Clinic',
  },
  {
    img: 'https://im8health.com/cdn/shop/files/Rectangle_3_68b5f4fc-fe48-466d-9d97-487fbdea1942.png?v=1764066245&width=300',
    name: 'Bobby Rich',
    title: 'Trainer to David Beckham and World-class Athletes',
  },
  {
    img: 'https://im8health.com/cdn/shop/files/Rectangle_4_9e90556f-68ae-405e-a707-89eff3d64066.png?v=1764066309&width=300',
    name: 'Dr. Suzanne Devkota',
    title: 'Gut Health Expert & Prof at Cedars Sinai',
  },
  {
    img: 'https://im8health.com/cdn/shop/files/Rectangle_5.png?v=1764066392&width=300',
    name: 'Tavi Castro',
    title: 'Breathwork Expert & Free-Diving World Record Holder',
  },
  {
    img: 'https://im8health.com/cdn/shop/files/Rectangle_7.png?v=1764066430&width=300',
    name: 'Dr. Amy Shah',
    title: 'Double-Board Certified Physician and Host of "Save Yourself" Podcast',
  },
  {
    img: 'https://im8health.com/cdn/shop/files/Rectangle_6.png?v=1764066459&width=300',
    name: 'Dr. Ara Suppiah',
    title: 'Performance & Longevity Physician at LIV Golf',
  },
]

const questions = [
  {
    q: 'Ingredients',
    a: 'Our comprehensive formula combines 92 nutrient-rich ingredients to fuel your body with everything it needs for optimal health. Packed with essential vitamins, minerals, antioxidants, superfoods, greens, pre-pro-post-biotics and clinical dosages of CoQ10 and MSM.*',
    des: 'View Supplement Facts',
  },
  {
    q: 'Third Party Tested',
    a: 'Every ingredient and dosage in IM8 is third-party tested. This guarantees that what you see on the label is what you get, so you know exactly what you’re putting into your body.',
  },
  {
    q: 'How to Enjoy',
    ol: [
      'Scoop out one serving (12 grams)',
      'Add 8-12 oz of cold water, juice, smoothie, or your favorite drink (Use less liquid for a stronger taste)',
      'Shake or blend well then enjoy',
    ],
  },
  {
    q: 'Tasting Notes',
    a: 'Experience a delightful blend with earthy undertones, a subtle tartness, and a hint of chocolate, culminating in a smooth acai and mixed berries finish.',
  },
]

const swiperContents = [
  'https://im8health.com/cdn/shop/files/preview_images/thm-expert_robinB2.jpg?v=1731999065',
  'https://im8health.com/cdn/shop/files/preview_images/influe-carou_bobbyRich2.jpg?v=1731863977',
  'https://im8health.com/cdn/shop/files/preview_images/thm-expert_amyShah2.jpg?v=1731864964',
  'https://im8health.com/cdn/shop/files/preview_images/thm-influ_dustinPoirier.jpg?v=1731833492',
  'https://im8health.com/cdn/shop/files/preview_images/image_54.png?v=1731863088',
  'https://im8health.com/cdn/shop/files/preview_images/1f4b2af008104c92a29f9d78814f1aa0.thumbnail.0000000000.jpg?v=1731860287',
]
</script>

<template>
  <div
    class="min-w-[630px] h-[2978px] laptop:max-w-[45%] laptop:w-[calc(45%-16px/2)] tablet:w-[calc(50%-16px/2)] max-w-[45%]! w-[45%]! grow shrink-0"
  >
    <section
      class="laptop:pt-0! p-[16px_0px_0_45px] max-w-full! flex flex-wrap mb-[2rem] list-none gap-[8px]"
    >
      <!-- STATS -->
      <div
        class="tablet:mt-0 flex flex-wrap items-center gap-[8px] text-[14px] font-medium text-(--primary-color-darker) m-[10px_0_14px_0]"
      >
        <div class="inline-flex gap-[6px] items-center align-middle">
          <!-- STARS -->
          <span class="inline-flex items-center gap-1">
            <StarCustomIcon
              v-for="(_, index) in 5"
              :key="index"
              class="size-[16px] drop-shadow-[0_1px_2px_rgba(164,0,17,0.3)] fill-(--primary-color)"
            />
          </span>
          <!-- END STARS -->
          <span class="font-semibold text-[14px] font-aeonik text-[#3d0008] tracking-[-0.02em]">
            4.8</span
          >
          <span class="font-semibold font-aeonik! text-[14px] text-[#3d0008] tracking-[-0.02em]">
            from 11,825 Reviews</span
          >
        </div>
        <div class="w-full xl:w-fit">
          <span class="text-[#d4c4b8] m-[0_2px] font-light">|</span>
          <span class="font-medium text-[#6b4c3a]" data-stat-type="purchases"
            >624k+ customer purchases</span
          >
          <span class="text-[#d4c4b8] m-[0_2px] font-light">|</span>
          <span class="font-medium text-[#6b4c3a]" data-stat-type="servings">19M+ servings</span>
        </div>
      </div>
      <!-- END STATS -->

      <!-- PRODUCT TITLE -->
      <div class="[word-break:break-word] m-[0_0_16px_0]!">
        <h1
          class="leading-[110%] text-(--primary-color-darker) text-[40px] font-normal tracking-[-.8px] m-0 font-arizona"
        >
          Daily Ultimate Essentials:<br />All-in-One Supplement
        </h1>
      </div>
      <!-- END PRODUCT TITLE -->

      <!-- PRODUCT DESCRIPTION -->
      <div class="m-[0px_0_12px_0]!">
        <div class="text-(--primary-color-darker) text-[16px] font-normal leading-[135%] m-0">
          <p class="pb-[12px] m-0">
            Engineered for peak absorption, this comprehensive formula replaces the need for 16
            daily supplements with 92 nutrient-rich ingredients in one delicious drink.*
          </p>
          <ul class="hidden">
            <li><strong>Energy:</strong> Unleash your natural energy</li>
            <li><strong>Immunity:</strong> Fortify your body's defence</li>
            <li><strong>Digest:</strong> Optimize your body’s digestive health</li>
          </ul>
        </div>
      </div>
      <!-- ENd PRODUCT DESCRIPTION -->

      <!-- CLINICALLY -->
      <div
        class="bg-[linear-gradient(135deg,_#f0f9f4_0%,_#e8f5ec_100%)] border-[1.5px] border-[#16A34A] rounded-[16px] p-[24px] mt-0 mb-4 w-full"
      >
        <div class="cpr-header flex justify-between items-start mb-[20px] gap-[12px]">
          <h3
            class="cpr-title font-arizona text-[22px] font-semibold text-[#50000b] m-0 leading-[1.2]"
          >
            Clinically Proven Results
          </h3>
          <span
            class="bg-[#0f7a3a] inline-flex items-center justify-center h-[25.891px] px-[15.178px] pt-[4.464px] pb-[3.427px] rounded-[17.856px] text-white text-[11px] font-bold uppercase tracking-[0.5px] whitespace-nowrap shrink-0"
            >90-DAY CLINICAL STUDY</span
          >
        </div>
        <div class="grid grid-cols-4 gap-[16px] mb-[16px]">
          <div class="flex flex-col items-start">
            <div class="flex flex-row items-baseline gap-[3px] mb-[4px]">
              <span class="text-[24px] leading-[1]">⚡</span>
              <span
                class="text-[#16A34A] font-arizona text-[26px] not-italic font-normal leading-[26px]"
                >95%</span
              >
            </div>
            <span class="text-[13px] font-medium text-(--primary-color-darker) leading-[1.3]"
              >More energy</span
            >
          </div>
          <div class="flex flex-col items-start">
            <div class="flex flex-row items-baseline gap-[3px] mb-[4px]">
              <span class="text-[24px] leading-[1]">🦠</span>
              <span
                class="text-[#16A34A] font-arizona text-[26px] not-italic font-normal leading-[26px]"
                >85%</span
              >
            </div>
            <span class="text-[13px] font-medium text-(--primary-color-darker) leading-[1.3]"
              >Better gut health</span
            >
          </div>
          <div class="flex flex-col items-start">
            <div class="flex flex-row items-baseline gap-[3px] mb-[4px]">
              <span class="text-[24px] leading-[1]">😴</span>
              <span
                class="text-[#16A34A] font-arizona text-[26px] not-italic font-normal leading-[26px]"
                >80%</span
              >
            </div>
            <span class="text-[13px] font-medium text-(--primary-color-darker) leading-[1.3]"
              >Better sleep quality</span
            >
          </div>
          <div class="flex flex-col items-start">
            <div class="flex flex-row items-baseline gap-[3px] mb-[4px]">
              <span class="text-[24px] leading-[1]">🧠</span>
              <span
                class="text-[#16A34A] font-arizona text-[26px] not-italic font-normal leading-[26px]"
                >70%</span
              >
            </div>
            <span class="text-[13px] font-medium text-(--primary-color-darker) leading-[1.3]"
              >Sharper focus</span
            >
          </div>
        </div>
        <p class="text-[11px] text-[#666] mb-[16px] italic">
          *Based on 12-week randomized controlled trial by San Francisco Research Institute
        </p>
        <div class="flex justify-between items-end gap-[16px]">
          <div class="flex-1">
            <button
              class="p-0 cursor-pointer font-aeonik! text-[14px] font-[600]! text-[#50000b] underline underline-offset-[3px] flex items-center gap-[6px] transition-opacity duration-200 ease"
            >
              Why These Results Matter?
              <ChevronDownCustom class="size-[12px] transition-transform ease duration-[0.3s]" />
            </button>
          </div>
          <div class="flex items-center gap-[8px] shrink-0">
            <img
              width="50"
              height="50"
              loading="lazy"
              :key="index"
              v-for="(image, index) in [
                '//im8health.com/cdn/shop/files/Vector_38d1c63f-d300-48b5-b6e6-084b0cf0086d.png?v=1764063546&amp;width=100',
                '//im8health.com/cdn/shop/files/NSF_CONTENTS_CERTIFIED_White_Vert_2.png?v=1764063546&amp;width=100',
                '//im8health.com/cdn/shop/files/b9a15702-8e60-441d-b1fd-ce12f6742dcb_svg.png?v=1764063545&amp;width=100',
              ]"
              :src="image"
              alt="Certification logo"
              class="h-[50px] w-auto object-contain"
            />
          </div>
        </div>
      </div>
      <!-- END CLINICALLY -->

      <!-- VARIANTS SELECT -->
      <div class="m-[16px_0] mt-0! block">
        <!-- SElECT FORM -->
        <div
          class="max-w-full! p-0 min-w-fit border-0 block min-w-min mx-[2px] border-[threedface] pt-[0.35em] pb-[0.625em] px-[0.75em]"
        >
          <!-- LEGEND -->
          <div
            class="text-[#50000b] text-[16px] font-bold leading-[1.35] pb-[8px] !m-0 pl-0 block tracking-0 [unicode-bidi:isolate] px-[2px]"
          >
            <div>1. Select Format:</div>
          </div>
          <!-- eND LEGEND -->

          <div class="flex flex-wrap laptop:grid grid-cols-2 [grid-gap:8px]">
            <!-- 1ST -->
            <div
              @click="currentFormSelectIndex = 'selectForm1'"
              ref="selectForm1"
              :class="{
                'filter-[saturate(.94)_brightness(.99)]! opacity-[.88]!':
                  currentFormSelectIndex !== selectForm1?.id,
              }"
              id="selectForm1"
              class="h-auto"
            >
              <label
                :class="{
                  ' border-(--primary-color-darker)! bg-[#f5eaea]!':
                    currentFormSelectIndex === selectForm1?.id,
                }"
                for=""
                class="transition-all duration-200 [box-shadow:0_3px_10px_-3px_#50000b1f]! filter-[saturate(1.12)_brightness(1.02)_contrast(1.02)] opacity-100 border border-[#e1cbb9] text-(--primary-color-darker) rounded-3xl p-0 w-full h-full will-change-[box-shadow,filter,opacity] backface-hidden [-webkit-font-smoothing:antialiased] relative isolate text-[20px] font-medium leading-[1.2] tracking-[-.4px] text-left flex items-center cursor-pointer!"
              >
                <img
                  src="//im8health.com/cdn/shop/files/UX-Input_1.jpg?v=8068906590217553853"
                  class="rounded-tl-[15px] rounded-bl-[15px] h-full object-cover h-[60px]"
                  width="60"
                  height="100%"
                  alt="ux input"
                />
                <div class="p-[16px_14px]">
                  <div
                    class="variant_best_value_new font-architekt absolute right-[16px] top-[-9px] bg-[#a40011] text-white text-center text-[10px] font-bold leading-[8px] uppercase px-[15px] py-[5px] tracking-[0] rounded-[20px]"
                  >
                    Most Popular
                  </div>
                  <div class="variant_option_top_new">
                    <span class="variant_name_new"> Forever Jar </span>
                  </div>
                  <div class="text-[12px] pt-[2px] leading-[1.35] font-medium">
                    (354g)

                    <span
                      class="variant_servings_price_new"
                      data-format-serving-price="true"
                      data-serving-count="90"
                      data-base-price="23500"
                    >
                      $2.61 USD / serving
                    </span>
                  </div>
                </div>
              </label>
            </div>
            <!-- END 1ST -->

            <!-- 2ND -->
            <div
              ref="selectForm2"
              id="selectForm2"
              class="h-auto cursor-pointer"
              :class="{
                'filter-[saturate(.94)_brightness(.99)]! opacity-[.88]!':
                  currentFormSelectIndex !== selectForm2?.id,
              }"
              @click="currentFormSelectIndex = 'selectForm2'"
            >
              <label
                for=""
                :class="{
                  'border-(--primary-color-darker)! bg-[#f5eaea]!':
                    currentFormSelectIndex === selectForm2?.id,
                }"
                class="cursor-pointer transition-all duration-200 [box-shadow:0_3px_10px_-3px_#50000b1f]! filter-[saturate(1.12)_brightness(1.02)_contrast(1.02)] opacity-100 border border-[#e1cbb9] text-(--primary-color-darker) rounded-3xl p-0 w-full h-full will-change-[box-shadow,filter,opacity] backface-hidden [-webkit-font-smoothing:antialiased] relative isolate text-[20px] font-medium leading-[1.2] tracking-[-.4px] text-left flex items-center"
              >
                <img
                  src="https://im8health.com/cdn/shop/files/UX-Input_2.jpg?v=4366596284312861834"
                  class="rounded-tl-[15px] rounded-bl-[15px] h-full object-cover h-[60px]"
                  width="60"
                  height="100%"
                  alt="ux input"
                />
                <div class="p-[16px_14px]">
                  <div class="variant_option_top_new">
                    <span class="variant_name_new"> Single-Serve Sachets</span>
                  </div>
                  <div class="text-[12px] pt-[2px] leading-[1.35] font-medium">
                    (354g)

                    <span
                      class="variant_servings_price_new"
                      data-format-serving-price="true"
                      data-serving-count="90"
                      data-base-price="23500"
                    >
                      $2.91 USD / serving
                    </span>
                  </div>
                </div>
              </label>
            </div>
            <!-- END 2ND -->
          </div>
        </div>
        <!-- END SElECT FORM -->

        <!-- 2. SUBSCRIBE & SAVE -->
        <div
          class="max-w-full! p-0 min-w-fit border-0 block min-w-min mx-[2px] border-[threedface] pt-[0.35em] pb-[0.625em] px-[0.75em]"
        >
          <!-- LEGEND -->
          <div
            class="text-[#50000b] text-[16px] font-bold leading-[1.35] pb-[8px] !m-0 pl-0 block tracking-0 [unicode-bidi:isolate] px-[2px]"
          >
            <div>2. Subscribe & Save:</div>
          </div>
          <!-- eND LEGEND -->

          <div class="flex flex-wrap flex-col [grid-gap:16px]">
            <!-- 1ST -->
            <div class="mt-[16px]">
              <label
                ref="selectSubscribe1"
                id="subscribeForm1"
                @click="currentSubscribeSelectIndex = 'subscribeForm1'"
                for=""
                :class="{
                  'border-[#A40011]!  [box-shadow:0_4px_12px_0_rgba(164,0,17,0.15)]! bg-linear-[120deg]! from-[rgba(245,234,234,0.80)]! from-0%! to-[rgba(255,242,237,0.60)]! to-100%! opacity-[.85]! filter-[saturate(1.18)_brightness(1.025)_contrast(1.03)]':
                    currentSubscribeSelectIndex === selectSubscribe1?.id,
                }"
                class="pt-[20px]! transition-all duration-[50ms] rounded-[16px] border border-[#50000b] text-[#50000b]! p-[16px] flex gap-[4px] m-0! text-[20px] font-medium leading-[1.2] tracking-[-.4px] text-left items-center relative cursor-pointer"
              >
                <span
                  v-if="currentSubscribeSelectIndex === selectSubscribe1?.id"
                  class="bg-[url(https://im8health.com/cdn/shop/t/121/assets/radio_fill.svg)] size-[24px] mb-auto filter-[saturate(1.2)_brightness(1.05)] shrink-0 min-w-[24px] mr-[4px]"
                ></span>
                <span
                  v-else
                  class="bg-[url(https://im8health.com/cdn/shop/t/121/assets/radio_blank.svg)] size-[24px] mb-auto filter-[saturate(1.2)_brightness(1.05)] shrink-0 min-w-[24px] mr-[4px]"
                ></span>
                <div class="w-full transition-colors duration-[.25s]">
                  <div
                    class="[box-shadow:0_2px_6px_-2px_#a4001140] filter-[saturate(1.15)_brightness(1.05)] font-architekt absolute left-[16px] bg-[#FEC63F] text-[#50000b] text-center font-bold uppercase tracking-0 rounded-[20px] backface-hidden top-[-11px] p-[6px_18px]! leading-[10px] text-[11px]"
                  >
                    NEW YEAR OFFER
                  </div>
                  <div
                    class="[box-shadow:0_2px_6px_-2px_#a4001140] filter-[saturate(1.15)_brightness(1.05)] font-architekt absolute right-[16px] bg-[#a40011] text-[#fff] text-center font-bold uppercase tracking-0 rounded-[20px] backface-hidden top-[-11px] p-[6px_18px]! leading-[10px] text-[11px]"
                  >
                    BEST VALUE
                  </div>
                  <!-- TITLE -->
                  <div class="flex justify-between items-center gap-[10px]">
                    <span class="font-arizona!">
                      90-Day Supply

                      <span style="color: #16a34a">(Save 30%)</span></span
                    >
                    <span class="text-[14px] font-bold text-right"
                      ><span class="formatted-price">$78</span>
                      <span class="opacity-[.6] [text-decoration:line-through]">
                        <span class="formatted-price"> $112 </span> </span
                      ><span class="variant_price_suffix">/mo</span></span
                    >
                  </div>
                  <!-- END TITLE -->

                  <!-- DES -->
                  <div
                    class="pb-[12px] border-b border-[#e1cbb9] flex justify-between gap-[10xp] text-[14px] text-[#50000b] font-medium leading-[1.35] pt-[2px] font-aeonik"
                  >
                    <span class="">Billed $235.00 USD every 12 weeks</span>

                    <span class="font-architekt text-[12px] font-bold"> $2.61 USD / serving </span>
                  </div>
                  <!-- END DES -->

                  <!-- LISt -->
                  <ul
                    class="list-none text-[14px] m-[12px_0_0_-20px] pl-0 [&>li]:relative [&>li]:mb-[6px] [&>li]:list-none! [&>li]:pl-0! [&>li]:ml-0!"
                  >
                    <li>🎓 Exclusive Access to 90 Day IM8 Transformation Program (see below)</li>
                    <li>💰 Maximum savings - lowest price per serving</li>
                    <li>👦 Share with family and friends</li>
                    <li>🎁 Free Daily Ultimate Mixer (US$18)</li>
                    <li>🚚 Free Shipping to US, UK, CA, and most of EU and APAC</li>
                    <li>⏸️ Cancel or pause anytime</li>
                    <li>🎁 Free Welcome Kit: Signature Red Cup + 5 Travel Sachets (US$18)</li>
                  </ul>
                  <!-- END LIST -->
                </div>
              </label>
            </div>
            <!-- END 1ST -->

            <!-- 2ND -->
            <div class="">
              <label
                ref="selectSubscribe2"
                id="subscribeForm2"
                @click="currentSubscribeSelectIndex = 'subscribeForm2'"
                for=""
                :class="{
                  'border-[#A40011]!  [box-shadow:0_4px_12px_0_rgba(164,0,17,0.15)]! bg-linear-[120deg]! from-[rgba(245,234,234,0.80)]! from-0%! to-[rgba(255,242,237,0.60)]! to-100%! bg-[#f5eaea]! opacity-[.85]! filter-[saturate(1.18)_brightness(1.025)_contrast(1.03)]':
                    currentSubscribeSelectIndex === selectSubscribe2?.id,
                }"
                class="pt-[20px]! transition-all duration-[50ms] rounded-[16px] border border-[#50000b] text-[#50000b]! p-[16px] flex gap-[4px] m-0! text-[20px] font-medium leading-[1.2] tracking-[-.4px] text-left items-center relative cursor-pointer"
              >
                <span
                  v-if="currentSubscribeSelectIndex === selectSubscribe2?.id"
                  class="bg-[url(https://im8health.com/cdn/shop/t/121/assets/radio_fill.svg)] size-[24px] mb-auto filter-[saturate(1.2)_brightness(1.05)] shrink-0 min-w-[24px] mr-[4px]"
                ></span>
                <span
                  v-else
                  class="bg-[url(https://im8health.com/cdn/shop/t/121/assets/radio_blank.svg)] size-[24px] mb-auto filter-[saturate(1.2)_brightness(1.05)] shrink-0 min-w-[24px] mr-[4px]"
                ></span>
                <div class="w-full transition-colors duration-[.25s]">
                  <!-- TITLE -->
                  <div class="flex justify-between items-center gap-[10px]">
                    <span class="font-arizona!">
                      30-Day Supply

                      <span style="">(Save 20%)</span></span
                    >
                    <span class="text-[14px] font-bold text-right"
                      ><span class="formatted-price">$89</span>
                      <span class="opacity-[.6] [text-decoration:line-through]">
                        <span class="formatted-price"> $112 </span> </span
                      ><span class="variant_price_suffix">/mo</span></span
                    >
                  </div>
                  <!-- END TITLE -->

                  <!-- DES -->
                  <div
                    class="pb-[12px] border-b border-[#e1cbb9] flex justify-between gap-[10xp] text-[14px] text-[#50000b] font-medium leading-[1.35] pt-[2px] font-aeonik"
                  >
                    <span class="">Billed $89.00 USD every 4 weeks</span>

                    <span class="font-architekt text-[12px] font-bold"> $2.97 USD / serving </span>
                  </div>
                  <!-- END DES -->

                  <!-- LISt -->
                  <ul
                    class="list-none text-[14px] m-[12px_0_0_-20px] pl-0 [&>li]:relative [&>li]:mb-[6px] [&>li]:list-none! [&>li]:pl-[20px] [&>li]:ml-0! [&>li]:before:content-[''] [&>li]:before:absolute [&>li]:before:left-0 [&>li]:before:top-[0px] [&>li]:before:bg-[url(https://im8health.com/cdn/shop/t/121/assets/sub_check.svg)] [&>li]:before:bg-no-repeat [&>li]:before:bg-center [&>li]:before:size-[16px] relative"
                  >
                    <li>30-day money back guarantee</li>
                    <li>Cancel or pause anytime</li>
                    <li>Free Shipping to US, UK, CA, and most of EU and APAC</li>
                    <li>Free Welcome Kit: Signature Red Cup + 5 Travel Sachets (US$18)</li>
                  </ul>
                  <!-- END LIST -->
                </div>
              </label>
            </div>
            <!-- END  2ND -->

            <!-- ONE TIME PURCHASE -->
            <div class="text-center m-0 p-0">
              <a
                :href="getURL"
                class="inline-block text-[14px] font-medium text-[#50000b] underline underline-offset-[3px] cursor-pointer transition-opacity duration-200 ease"
              >
                One Time Purchase
                <span class="font-medium">
                  <span class="formatted-price"> $112 </span>
                </span>
              </a>
            </div>
            <!-- END ONE TIME PURCHASE -->
          </div>
        </div>
        <!-- END 2. SUBSCRIBE & SAVE -->
      </div>
      <!-- END VARIANTS SELECT -->

      <!-- BUY BUTTON MAIN -->
      <div class="min-h-[48px] m-0! w-full">
        <div class="m-[-10px_0px_12px_0]!">
          <button
            class="flex! m-0 h-[48px] p-[5px] relative transition-none w-full justify-center items-center border-0 cursor-pointer [font:inherit] no-underline appearance-none font-aeonik rounded-[100px] bg-[#a40011] py-[13px] px-[17px] min-w-[272px] text-white text-[16px] font-bold! leading-[22px] tracking-[0.32px] uppercase"
          >
            <span class="button-text">START MY 90-DAY TRANSFORMATION PROGRAM</span>
            <span class="dash_new"> – </span>
            <span class="product_price_new" id="price2-template--17653238202535__main" role="status"
              >$78.33 USD/mo</span
            >
          </button>
        </div>
      </div>
      <!-- END BUY BUTTON MAIN -->

      <!-- GREEN -->
      <div
        class="py-[14px] px-[18px] bg-[linear-gradient(135deg,#f0fdf4_0%,color-mix(in_srgb,#f0fdf4_80%,#22c55e_20%)_100%)] border-[1.5px] border-solid border-[#22c55e] rounded-[12px] flex items-center gap-[12px] shadow-[0_2px_8px_rgba(0,0,0,0.08)] transition-[opacity,max-height] duration-300 ease overflow-hidden w-full"
      >
        <div
          class="size-[24px] bg-[#22c55e] text-white rounded-full flex items-center justify-center shrink-0"
        >
          <svg
            class="size-[14px]"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="2.5"
            stroke="currentColor"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"></path>
          </svg>
        </div>
        <div class="text-[14px] font-medium text-[#166534] leading-[1.4]">
          <span class="font-bold">New Year discount</span>
          automatically applied at checkout
        </div>
      </div>
      <!-- END GREEN -->

      <!-- 90DAYS -->
      <div
        class="border-2 border-[#BF9C74] bg-[linear-gradient(171deg,#FFEFD6_6.83%,rgba(255,238,219,0.50)_135.82%)] shadow-[0_4px_12px_0_rgba(217,119,6,0.12)] rounded-[20px] py-[28px] px-[24px] mt-[16px] w-full"
      >
        <div class="text-center">
          <div
            class="inline-flex items-center justify-center gap-[6px] bg-[linear-gradient(90deg,#EEB87A_0%,#DFCE89_100%)] rounded-[20px] py-[8px] px-[16px] text-[12px] font-bold text-[#50000b] uppercase tracking-[0.5px] mt-0 mx-auto mb-[16px]"
          >
            <span class="text-[14px]">🎓</span>
            <span>90-DAY MEMBERS ONLY</span>
          </div>
          <h3 class="text-[28px] font-medium text-[#50000B] m-0 mb-[8px] leading-[1.2] text-center">
            90-Day IM8 Transformation Program
          </h3>
          <p class="text-[14px] font-medium text-[#50000B] m-0 mb-[20px] leading-[1.5] text-center">
            Exclusive access to quarterly masterclasses with our world-class Medical and Performance
            Experts
          </p>
        </div>
        <div class="grid grid-cols-3 gap-[16px] mb-[20px]">
          <a
            v-for="(expert, index) in tpExperts"
            :key="index"
            :src="expert.img"
            class="hover:-translate-y-0.75 flex flex-col items-center text-center no-underline rounded-[12px] p-[8px] m-[-8px] transition-transform duration-500 ease-[cubic-bezier(0.23,1,0.32,1)]"
          >
            <img
              :src="expert.img"
              :alt="expert.img"
              class="hover:border-[#a57d52] hover:[box-shadow:0_6px_18px_-4px_rgba(165,125,82,0.4)] w-full aspect-square rounded-[12px] object-cover mb-[10px] border-2 border-[#BF9C74] shadow-[0_2px_8px_-2px_rgba(0,0,0,0.08)] transition-[border-color,box-shadow] duration-500 ease-[cubic-bezier(0.23,1,0.32,1)]"
            />
            <p
              class="text-[13px] font-bold text-[#50000b] m-0 mb-[4px] leading-[1.3] transition-colors duration-500 ease-[cubic-bezier(0.23,1,0.32,1)]"
            >
              {{ expert.name }}
            </p>
            <p class="text-[11px] font-normal text-[#6b4c3a] m-0 leading-[1.4]">
              {{ expert.title }}
            </p>
          </a>
        </div>
        <p
          class="text-[13px] font-medium text-[#50000b] text-center leading-[1.5] m-0 pt-[16px] border-t border-[rgba(191,156,116,0.3)]"
        >
          Get personalized guidance, exclusive content, and direct access to leading experts in
          health optimization, performance, and longevity.
        </p>
        <a
          :href="getURL"
          class="flex items-center justify-center gap-[8px] w-full mt-[16px] py-[12px] px-[20px] bg-[linear-gradient(90deg,#EEB87A_0%,#DFCE89_100%)] border-0 rounded-[12px] text-[13px] font-bold text-[#50000b] no-underline uppercase tracking-[0.5px] cursor-pointer relative overflow-hidden isolate shadow-[0_2px_8px_-2px_rgba(191,156,116,0.25),inset_0_1px_0_rgba(255,255,255,0.3)] transition-[box-shadow] duration-400 ease-[cubic-bezier(0.4,0,0.2,1)] before:content-[''] before:absolute before:top-0 before:left-[-100%] before:w-full before:h-full before:bg-[linear-gradient(90deg,transparent_0%,rgba(255,255,255,0.35)_50%,transparent_100%)] before:transition-[left] before:duration-[600ms] before:ease-[cubic-bezier(0.4,0,0.2,1)] before:z-[1] before:cursor-pointer hover:before:left-[100%] after:content-[''] after:absolute after:inset-[-2px] after:rounded-[inherit] after:bg-[linear-gradient(135deg,rgba(238,184,122,0.5)_0%,rgba(223,206,137,0.3)_50%,rgba(238,184,122,0.5)_100%)] after:opacity-0 after:-z-[1] after:transition-opacity after:duration-400 after:ease after:blur-[8px] hover:after:opacity-100"
        >
          <span class="relative z-2">Learn More About the Program</span>
          <ChevronDownCustom class="-rotate-90 relative z-2 shrink-0" />
        </a>
      </div>
      <!-- END 90DAYS -->

      <!-- 30DAYS 100% -->
      <div
        class="bg-[#F0FDF4] border-2 border-[#16A34A] rounded-[16px] py-[20px] px-[24px] my-[16px] flex items-center gap-[16px] w-full mt-[10px]!"
      >
        <div class="shrink-0 size-[36px] flex items-center justify-center">
          <img
            class="size-[36px]"
            src="//im8health.com/cdn/shop/files/greencheck.png?v=1764066515&amp;width=72"
            alt="Guarantee"
            loading="lazy"
          />
        </div>
        <div class="flex-1">
          <h4
            class="font-[var(--font-abc-arizona-flare)] text-[20px] font-semibold text-[#50000b] m-0 mb-[4px] leading-[1.2]"
          >
            30-Day 100% Money Back Guarantee
          </h4>
          <p class="text-[13px] font-normal text-[#50000b] m-0 leading-[1.4]">
            We're so confident you'll love it, take a full 30 days to decide
          </p>
        </div>
      </div>
      <!-- END 30DAYS 100% -->

      <!-- PAY WITH HSA/FSA -->
      <div class="w-full flex items-center justify-center gap-[5px] text-[12px] text-[#50000b]">
        <span class="text-(--primary-color-darker) font-bold">Pay with HSA/FSA</span>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="19"
          height="19"
          viewBox="0 0 19 19"
          fill="none"
        >
          <g clip-path="url(#clip0_4962_240)">
            <mask
              id="mask0_4962_240"
              style="mask-type: luminance"
              maskUnits="userSpaceOnUse"
              x="0"
              y="0"
              width="19"
              height="19"
            >
              <path d="M0.453613 0.639894H18.5366V18.7229H0.453613V0.639894Z" fill="white"></path>
            </mask>
            <g mask="url(#mask0_4962_240)">
              <path
                d="M9.42359 3.96507C8.52032 3.96507 7.78809 4.69731 7.78809 5.60058C7.78809 6.50385 8.52032 7.23608 9.42359 7.23608C10.3269 7.23608 11.0591 6.50385 11.0591 5.60058C11.0582 4.69762 10.3265 3.96595 9.42359 3.96507Z"
                fill="#50000B"
              ></path>
              <path
                d="M8.97401 10.1572L4.25241 15.0868C3.12222 13.9971 2.36465 12.5785 2.08768 11.0331C2.03484 10.7432 1.99865 10.4505 1.97928 10.1564L8.97401 10.1572ZM2.03348 8.64283C2.48571 5.42538 4.94758 2.85911 8.14351 2.27377C8.59471 2.19119 9.05252 2.14959 9.51121 2.14943C13.2631 2.15708 16.4367 4.92644 16.9523 8.64283H2.03348ZM13.5322 16.044C11.0621 17.6042 7.91341 17.5985 5.44875 16.0297L9.48332 11.8174L13.5322 16.044ZM17.0113 10.1572C16.9261 11.5224 16.4701 12.8386 15.6923 13.9638C15.4084 14.3737 15.0851 14.755 14.727 15.102L9.99102 10.1604L17.0113 10.1572ZM14.6409 2.24189C10.5327 -0.597452 4.90056 0.431274 2.0613 4.53948C-0.778042 8.64777 0.250684 14.2799 4.35889 17.1192C8.46503 19.957 14.0939 18.931 16.9347 14.827C19.7715 10.7172 18.7453 5.08648 14.6409 2.24189Z"
                fill="#50000B"
              ></path>
            </g>
          </g>
          <defs>
            <clipPath id="clip0_4962_240">
              <rect
                width="18.083"
                height="18.083"
                fill="white"
                transform="translate(0.453613 0.639893)"
              ></rect>
            </clipPath>
          </defs>
        </svg>
        <span>Save an average of 30%</span>
        <a :href="getURL" class="underline font-bold cursor-pointer">Learn more</a>
      </div>
      <!-- END PAY WITH HSA/FSA -->

      <!-- ACCORDION -->
      <div class="m-[8px_0_24px_0]! w-full">
        <div class="p-0 m-0 border-0">
          <ul class="m-0 list-none p-0">
            <li
              v-for="(q, index) in questions"
              :key="index"
              class="m-0 border-b border-(--primary-color-darker)"
            >
              <!-- QUESTION -->
              <div
                @click="toggleQuestion(index)"
                class="border-0 py-[16px] cursor-pointer relative"
              >
                <h4
                  :class="
                    openQuestionIndex === index
                      ? 'bg-[url(https://im8health.com/cdn/shop/t/121/assets/product_banner_minus.svg)]'
                      : 'bg-[url(https://im8health.com/cdn/shop/t/121/assets/product_banner_plus.svg)]'
                  "
                  class="font-aeonik bg-no-repeat bg-right text-[#50000b] text-[16px] font-bold leading-[1.35] m-0 transition-all duration-300"
                >
                  {{ q.q }}
                </h4>
              </div>
              <!-- END QUESTION -->
              <!-- ANSWER -->
              <div
                v-show="openQuestionIndex === index"
                class="pb-[16px] relative text-[#50000b] text-[16px] font-normal leading-[1.35] overflow-hidden transition-all duration-300"
              >
                <div v-if="q?.a">
                  <p class="m-[0_0_12px_0] last:m-0!">{{ q.a }}</p>
                </div>
                <div v-if="q?.des" class="mt-[12px]">
                  <div
                    class="text-[#50000b] text-[16px] font-normal leading-[1.35] underline underline-offset-[4px] cursor-pointer"
                  >
                    {{ q.des }}
                  </div>
                </div>

                <ol v-if="q?.ol" class="list-decimal pl-[26px]">
                  <li v-for="(item, index) in q.ol" :key="index">
                    {{ item }}
                  </li>
                </ol>
              </div>
              <!-- END ANSWER -->
            </li>
          </ul>
        </div>
      </div>
      <!-- END ACCORDION -->

      <!-- IM8 AMBASSADORS -->
      <div class="my-[24px] w-full">
        <div
          class="font-arizona text-[#50000b] text-[20px] font-medium leading-[1.2] tracking-[-.4px]"
        >
          What our IM8 Ambassadors are saying
        </div>
        <swiper
          direction="horizontal"
          :slides-per-view="5.14"
          :space-between="10"
          :mousewheel="{ forceToAxis: true }"
          :grab-cursor="true"
          :slides-per-group="1"
          :free-mode="true"
          :modules="modules"
          class="pt-[16px]!"
        >
          <swiper-slide v-for="(url, index) in swiperContents" :key="index">
            <div>
              <div class="cursor-pointer h-[168px] relative">
                <img
                  @click="handleOpenVideoSwiper(index)"
                  class="absolute w-full object-cover inset-0 h-full! rounded-[8px]"
                  :src="url"
                  alt=""
                />
                <svg
                  class="absolute bottom-[12px] right-[12px] z-1 size-[24px] fill-none"
                  width="24"
                  height="24"
                  viewBox="0 0 24 24"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                  style="display: block"
                >
                  <circle cx="11.75" cy="12.25" r="9.25" fill="#50000B"></circle>
                  <g clip-path="url(#clip0_779_10354)">
                    <path
                      fill-rule="evenodd"
                      clip-rule="evenodd"
                      d="M20.4865 3.51351L12 0L3.51351 3.51351L0 12L3.51351 20.4865L12 24L20.4865 20.4865L24 12L20.4865 3.51351ZM9.75 15.8971L16.5 12L9.75 8.10289V15.8971Z"
                      fill="white"
                    ></path>
                  </g>
                  <defs>
                    <clipPath id="clip0_779_10354">
                      <rect width="24" height="24" fill="white"></rect>
                    </clipPath>
                  </defs>
                </svg>
              </div>
            </div>
          </swiper-slide>
        </swiper>
        <SwiperVideoPopup
          :on-close="
            () => {
              openVideoSwiper = false
              body.style.overflow = 'auto'
            }
          "
          v-if="openVideoSwiper"
          :video-index="openVideoIndex"
        />
        <BackdropBlur v-show="openVideoSwiper" />
      </div>
      <!-- END IM8 AMBASSADORS -->
    </section>
  </div>
</template>
