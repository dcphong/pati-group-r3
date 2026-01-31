<template>
  <div
    v-if="open"
    class="fixed bottom-0 z-2 left-0 right-0 bg-[#f9f9f9] p-5 text-center border-t border-[#ccc]"
  >
    <p class="py-[20px]">
      We use cookies to improve your experience. By using our site, you agree to our use of cookies.
      Learn more in our <a href="/pages/cookie-policy" style="color: #007bff">Cookies Policy</a>.
    </p>
    <button
      class="rounded-full bg-[#a52a2a] text-white border-0 py-2 px-8 text-[16px] cursor-pointer font-bold uppercase mt-2.5"
      @click="handleAcceptCookies"
    >
      Accept
    </button>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

const open = ref<boolean>(true)
const handleAcceptCookies = () => {
  open.value = false
}
</script>
