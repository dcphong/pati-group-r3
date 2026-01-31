<script setup lang="ts">
import { X } from 'lucide-vue-next'
</script>

<template>
  <div
    class="rounded-full border border-black/50 flex justify-center items-center"
    :class="`size-7 hover:scale-110 transition-all duration-300`"
  >
    <X :size="12" />
  </div>
</template>
