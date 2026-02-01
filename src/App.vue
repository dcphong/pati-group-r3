<template>
  <main>
    <header-base />
    <global-banner
      :class="isShowBanner ? 'translate-y-0' : '-translate-y-40'"
      class="transition-transform duration-500 -translate-y-40 fixed top-0"
    />
    <main-content />
    <daily-ultimates-essentials-fixed />
    <accept-cookie />
  </main>
</template>

<script setup lang="ts">
import HeaderBase from '@/components/header/HeaderBase.vue'
import AcceptCookie from '@/components/popup/AcceptCookie.vue'
import MainContent from '@/components/main/MainContent.vue'
import GlobalBanner from './components/GlobalBanner.vue'
import { onMounted, onUnmounted, ref } from 'vue'
import DailyUltimatesEssentialsFixed from './components/main/DailyUltimatesEssentialsFixed.vue'

const isShowBanner = ref<boolean>(false)
const globalBanner = ref<HTMLElement | null>(null)

const handleScroll = () => {
  window.addEventListener('scroll', () => {
    if (window.scrollY > 300) {
      isShowBanner.value = true
    } else {
      isShowBanner.value = false
    }
  })
}
onMounted(() => {
  if (window.scrollY > 300) {
    isShowBanner.value = true
  }

  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped></style>
