<script setup lang="ts">
const items = ['About Us', 'Our Impact', 'Quality and Standards', 'The Healthspan Blog']
</script>

<template>
  <div class="p-0 bg-white border-0 rounded-b-xl ml-1 text-left [box-shadow:0_0_0]">
    <ul class="p-[3px_16px_6px_16px] w-full m-0 list-none block page-width space-y-[6px]">
      <li v-for="(item, index) in items" :key="index">
        <a
          href="#"
          class="font-aeonik p-[6px_0] text-[16px] font-medium leading-[135%] tracking-[0] text-(--primary-color-darker) hover:underline hover:underline-offset-[5px] decoration-2"
        >
          <div>{{ item }}</div>
        </a>
      </li>
    </ul>
  </div>
</template>
