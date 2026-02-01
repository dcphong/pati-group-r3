<script setup lang="ts">
import ChevronDownCustom from '@/components/icon/ChevronDownCustom.vue'
import MenuDropdownNav from '@/components/header/MenuDropdownNav.vue'
import DiscoverDropdownItems from '@/components/header/DiscoverDropdownItems.vue'
import UserCustomIcon from '@/components/icon/UserCustomIcon.vue'
import CartCustomIcon from '@/components/icon/CartCustomIcon.vue'
import getURL from '@/utils'

const routerPaths = ['Shop', 'Science', 'The Beckham Stack', 'Welcome from David']
const rightNavItems = ['Reviews', 'Ingredients', 'Discover']
</script>

<template>
  <div
    class="page-width laptop:px-[50px] tablet:px-[3.2rem] flex justify-between items-center gap-8 py-0"
  >
    <nav class="block ml-[clamp(-8px,-1vw,-20px)]! w-[calc(50%-50px)]">
      <ul class="list-none p-0 m-0 inline-flex flex-wrap laptop:flex-nowrap">
        <li
          v-for="(path, index) in routerPaths"
          :key="index"
          class="m-0 p-0"
          :class="{
            group: index === 0,
          }"
        >
          <a
            :href="getURL"
            :class="`peer/${index}`"
            class="flex items-center laptop:p-[21px_clamp(8px,1.2vw,20px)]! text-[clamp(13px,1vw,16px)]! whitespace-nowrap font-aeonik py-[21px] px-[20px] text-[16px] font-[500] leading-[22px] tracking-[0] no-underline text-(--primary-color-darker)"
          >
            <span class="relative group peer/shop">
              {{ path }}
              <div
                class="underline-bounce bg-(--primary-color-darker) h-0.75 w-full absolute -bottom-2 left-0"
              ></div>
            </span>
            <chevron-down-custom
              v-if="index === 0"
              class="text-(--primary-color-darker) size-5 ml-2 group-hover:rotate-180 transition-transform duration-300"
            />
          </a>
          <menu-dropdown-nav
            class="peer-hover/0:visible! peer-hover/0:opacity-100 delay-200 duration-300 -translate-y-8 peer-hover/0:translate-y-2 hover:opacity-100 hover:visible hover:translate-y-2 opacity-0 transition-all invisible z-5"
            v-if="index === 0"
          />
        </li>
      </ul>
    </nav>
    <!-- LOGO -->
    <a :href="getURL" class="text-center p-0 p-[.75rem]">
      <div class="w-full ml-0 inline-block h-fit align-bottom">
        <img
          src="//im8health.com/cdn/shop/files/Header-Logo-New.svg?v=1729066833&amp;width=600"
          alt="IM8 Health"
          srcset="
            //im8health.com/cdn/shop/files/Header-Logo-New.svg?v=1729066833&amp;width=95   95w,
            //im8health.com/cdn/shop/files/Header-Logo-New.svg?v=1729066833&amp;width=143 143w,
            //im8health.com/cdn/shop/files/Header-Logo-New.svg?v=1729066833&amp;width=190 190w
          "
          class="max-w-full h-auto"
          width="95"
          height="24.562737642585553"
          loading="eager"
          sizes="(min-width: 750px) 95px, 50vw"
        /></div
    ></a>
    <!-- END LOGO -->
    <div class="flex items-center gap-4 w-[calc(50%-50px)] justify-end">
      <nav class="block">
        <ul class="list-none p-0 m-0 inline-flex flex-wrap laptop:flex-nowrap">
          <li v-for="(path, index) in rightNavItems" :key="index" class="m-0 p-0 group">
            <a
              href="#"
              :class="`peer/${index}`"
              class="flex items-center laptop:p-[21px_clamp(8px,1.2vw,20px)]! text-[clamp(13px,1vw,16px)]! whitespace-nowrap font-aeonik py-[21px] px-[20px] text-[16px] font-[500] leading-[22px] tracking-[0] no-underline text-(--primary-color-darker) relative"
            >
              <span class="relative group">
                {{ path }}
                <div
                  class="underline-bounce bg-(--primary-color-darker) h-0.75 w-full absolute -bottom-2 left-0"
                ></div>
              </span>
              <chevron-down-custom
                v-if="index === 2"
                class="text-(--primary-color-darker) size-5 ml-2 group-hover:rotate-180 transition-transform duration-300"
              />
              <discover-dropdown-items
                v-if="index === 2"
                class="invisible group-hover:visible absolute -bottom-[calc(30px+100%)] -left-[28%]"
              />
            </a>
          </li>
        </ul>
      </nav>
      <!-- ACCOUNT & CART -->
      <div class="flex items-center laptop:shrink-0 laptop:gap-3! pr-0 pl-1.75">
        <user-custom-icon />
        <div class="relative">
          <cart-custom-icon />

          <span
            class="absolute top-0 right-5 font-aeonik text-lg h-full flex items-center justify-center text-center font-bold text-[12px] text-(--primary-color-darker)"
            >0</span
          >
        </div>
      </div>
      <!-- END ACCOUNT & CART -->
    </div>
  </div>
</template>
