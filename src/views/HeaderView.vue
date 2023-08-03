<template lang="">
  <h1 class="text-white lg:text-5xl text-3xl font-semibold flex items-center gap-2">
    <img src="../assets/icons/hand.svg" class="lg:block hidden" alt="" />
    <span>Hey</span>
    <span>
      <input
        type="text"
        class="bg-inherit border-none outline-none"
        @input="saveName"
        v-model="userName"
        placeholder="Enter name..."
      />
    </span>
  </h1>
</template>
<script setup>
import { useStorage } from '@vueuse/core'
const userName = useStorage('name', '')
</script>
<style></style>
