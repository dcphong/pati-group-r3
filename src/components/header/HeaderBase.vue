<script setup lang="ts">
import SaleAnnouncement from '@/components/header/SaleAnnouncement.vue'
import LocalePicker from '@/components/header/LocalePicker.vue'
import NavigationBase from '@/components/header/NavigationBase.vue'
</script>

<template>
  <header>
    <div
      class="bg-(--primary-color) no-underline text-(--white-color) block cursor-pointer pt-[8px] pb-[9px] relative z-3"
    >
      <sale-announcement />
      <locale-picker />
    </div>
    <!-- NAVIGATION -->
    <navigation-base />
    <!-- END NAVIGATION -->
  </header>
</template>
