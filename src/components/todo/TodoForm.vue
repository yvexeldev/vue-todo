<template>
  <div>
    <form @submit.prevent class="flex lg:gap-3 gap-2 items-center justify-between">
      <input
        type="text"
        v-model="todoName"
        placeholder="Todo Title..."
        class="bg-gray-800 lg:p-2.5 p-1.5 lg:text-2xl text-xl font-bold rounded-md text-white outline-none w-3/4 border border-gray-800"
      />
      <button
        @click="
          () => {
            saveTodo(todoName)
            todoName = ''
          }
        "
        type="submit"
        class="border-green-500 border rounded-md lg:p-2.5 p-1.5 font-bold lg:text-2xl text-xl w-1/4 text-green-500 duration-300 hover:bg-green-500 hover:text-white"
      >
        Add
      </button>
    </form>
  </div>
</template>
<script setup>
import { ref } from 'vue'
const todoName = ref('')
// eslint-disable-next-line no-unused-vars
const props = defineProps({
  saveTodo: {
    type: Function,
    required: true
  }
})
</script>
<style></style>
