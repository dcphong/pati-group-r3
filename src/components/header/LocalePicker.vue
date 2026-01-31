<template>
  <div
    ref="dropdownRef"
    class="absolute top-[6px] text-[14px] right-[100px] font-architekt font-bold"
  >
    <button
      class="group cursor-pointer flex justify-end items-end relative"
      @click="handleOpenDropdown"
    >
      <span class="group-hover:underline">{{ currencyCode[currentCurrency] }}</span>
      <chevron-down-custom
        class="mb-2"
        :class="{
          'rotate-180': open,
        }"
      />
    </button>
    <transition
      name="fade-down"
      enter-active-class="transition-all duration-300 ease-out"
      enter-from-class="opacity-0 -translate-y-5"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition-all duration-100 ease-in"
      leave-from-class="opacity-100 translate-y-0"
    >
      <div
        v-if="open"
        class="min-h-[273px] min-w-[255px] bg-white border border-[rgba(80,0,11,0.1)] absolute right-0 top-13"
      >
        <div
          class="h-[68px] flex justify-end text-center gap-[.5rem] pt-[1.5rem] pb-[0.6rem] px-[1.5rem] flex-col sticky -top-[.02rem] bg-[rgba(255,255,255)] z-6"
        >
          <div class="relative w-full flex">
            <label
              for="search"
              class="absolute top-3 left-[2rem] text-base z-5 text-(--link-color) transition-all duration-200"
              :class="{
                'text-2xl! top-5': !isFocused && !inputValue,
              }"
              >search</label
            >
            <input
              id="search"
              type="text"
              class="border border-(--link-color) pt-[2.2rem] pr-[1.5rem] pb-[.8rem] pl-[2rem] outline-(--primary-color-darker) outline-offset-3 rounded-none! text-(--primary-color-darker) min-w-full font-aeonik! font-[400] text-[1.6rem] h-[4.5rem]"
              @focus="isFocused = true"
              @blur="isFocused = false"
              @input="handleInputChange"
              :value="inputValue"
            />
            <search
              v-if="!inputValue && !isFocused"
              class="text-black stroke-1 absolute size-8 top-5 right-5"
            />
            <circle-x-custom
              v-if="inputValue"
              :size="16"
              :outer-size="30"
              class="absolute top-5 right-5 text-black"
              @click="inputValue = ''"
            />
          </div>
        </div>
        <!-- COUNTRIES -->
        <div class="max-h-[205px] overflow-y-scroll text-(--link-color)">
          <ul class="pt-[.6rem]">
            <li
              v-for="(currency, index) in currencies"
              :key="index"
              @click="() => handleChangeCurrency(currency.label)"
              class="flex justify-between gap-[.5rem] py-[.9rem] px-[1.5rem] no-underlinen leading-[calc(1+.8/1.0)] text-(--primary-color-darker) wrap-break-word text-start! items-center group"
            >
              <div class="size-5 flex justify-center items-center">
                <check
                  class="invisible size-5"
                  :class="{ visible: currentCurrency === currency.label }"
                />
              </div>
              <div class="flex justify-start w-full">
                <span>{{ currency.label }}</span>
              </div>
              <div
                class="text-end invisible group-hover:visible duration-300 transition-all opacity-0 group-hover:opacity-100 space-x-2"
              >
                <span>{{ currency.currency }}</span>
                <span>{{ currencySymbols[currency.currency] }}</span>
              </div>
            </li>
          </ul>
        </div>
        <!-- END COUNTRIES -->
        <div class="h-full"></div>
      </div>
    </transition>
  </div>
</template>

<script setup lang="ts">
import ChevronDownCustom from '@/components/icon/ChevronDownCustom.vue'
import { Check, Search } from 'lucide-vue-next'
import { ref, onMounted, onUnmounted } from 'vue'
import CircleXCustom from '../icon/CircleXCustom.vue'
const open = ref<boolean>(false)
const currentCurrency = ref<string>('United States')
const isFocused = ref<boolean>(false)
const inputValue = ref<string>('')
const dropdownRef = ref<HTMLElement | null>(null)

const handleOpenDropdown = () => {
  open.value = !open.value
}

const handleClickOutside = (event: MouseEvent) => {
  if (dropdownRef.value && !dropdownRef.value.contains(event.target as Node)) {
    open.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', handleClickOutside)
})

onUnmounted(() => {
  document.removeEventListener('click', handleClickOutside)
})

const handleChangeCurrency = (currency: string) => {
  currentCurrency.value = currency
  open.value = false
}
const handleInputChange = (e: Event) => {
  const target = e.target as HTMLInputElement
  inputValue.value = target.value
}

const currencyCode = <Record<string, string>>{
  Australia: 'AUD',
  Belgium: 'EUR',
  Canada: 'CAD',
  France: 'EUR',
  Germany: 'EUR',
  'Hong Kong Sar': 'HKD',
  Hungary: 'HUF',
  Indonesia: 'IDR',
  Israel: 'ILS',
  Italy: 'EUR',
  JAPAN: 'JPY',
  Lithuania: 'EUR',
  Malaysia: 'MYR',
  Netherlands: 'EUR',
  'New Zealand': 'NZD',
  Philippines: 'PHP',
  Poland: 'PLN',
  Romania: 'RON',
  'Saudi Arabia': 'SAR',
  Singapore: 'SGD',
  'South Korea': 'KRW',
  Sweden: 'SEK',
  Switzerland: 'CHF',
  Taiwan: 'TWD',
  'United Arab Emirates': 'AED',
  'United Kingdom': 'GBP',
  'United States': 'USD',
}

const currencySymbols = <Record<string, string>>{
  AUD: 'A$',
  CAD: 'C$',
  CHF: 'CHF',
  EUR: '€',
  GBP: '£',
  HKD: 'HK$',
  HUF: 'Ft',
  IDR: 'Rp',
  ILS: '₪',
  JPY: '¥',
  MYR: 'RM',
  NZD: 'NZ$',
  PHP: '₱',
  PLN: 'zł',
  RON: 'lei',
  SAR: 'ر.س',
  SGD: 'S$',
  KRW: '₩',
  SEK: 'kr',
  TWD: 'NT$',
  AED: 'د.إ',
  USD: '$',
}
const currencies: { currency: string; label: string }[] = [
  {
    currency: 'AUD',
    label: 'Australia',
  },
  {
    currency: 'EUR',
    label: 'Belgium',
  },
  {
    currency: 'CAD',
    label: 'Canada',
  },
  {
    currency: 'EUR',
    label: 'France',
  },
  {
    label: 'Germany',
    currency: 'EUR',
  },
  {
    label: 'Hong Kong Sar',
    currency: 'HKD',
  },
  {
    currency: 'HUF',
    label: 'Hungary',
  },
  {
    label: 'Indonesia',
    currency: 'IDR',
  },
  {
    label: 'Israel',
    currency: 'ILS',
  },
  {
    label: 'Italy',
    currency: 'EUR',
  },
  {
    label: 'JAPAN',
    currency: 'JPY',
  },
  {
    label: 'Lithuania',
    currency: 'EUR',
  },
  {
    label: 'Malaysia',
    currency: 'MYR',
  },
  {
    label: 'Netherlands',
    currency: 'EUR',
  },
  {
    label: 'New Zealand',
    currency: 'NZD',
  },
  {
    label: 'Philippines',
    currency: 'PHP',
  },
  {
    label: 'Poland',
    currency: 'PLN',
  },
  {
    label: 'Romania',
    currency: 'RON',
  },
  {
    label: 'Saudi Arabia',
    currency: 'SAR',
  },
  {
    label: 'Singapore',
    currency: 'SGD',
  },
  {
    label: 'South Korea',
    currency: 'KRW',
  },
  {
    label: 'Sweden',
    currency: 'SEK',
  },
  {
    label: 'Switzerland',
    currency: 'CHF',
  },
  {
    label: 'Taiwan',
    currency: 'TWD',
  },
  {
    label: 'United Arab Emirates',
    currency: 'AED',
  },
  {
    label: 'United Kingdom',
    currency: 'GBP',
  },
  {
    label: 'United States',
    currency: 'USD',
  },
]
</script>
