<template>
  <div
    @click="changeTodo(todo)"
    class="lg:p-3 p-1.5 rounded-md cursor-pointer duration-300 bg-gray-700 lg:text-2xl text-xl flex gap-3 justify-between items-center text-white"
  >
    <div class="flex items-center lg:gap-3 gap-2 py-2">
      <span
        :class="todo.isCompleted ? 'bg-green-500' : ''"
        class="lg:ml-1 ml-1 lg:p-1.5 p-0.5 border-4 block duration-300 cursor-pointer outline-green-500 outline border-gray-700 hover:bg-green-500 rounded-full"
      ></span>

      <h1 :class="todo.isCompleted ? 'text-green-500 line-through' : ''" class="font-bold">
        {{ todo.title }}
      </h1>
    </div>
    <img
      src="../../assets/icons/trash.svg"
      class="text-2xl font-black text-red-500"
      @click="deleteTodo(todo)"
    />
  </div>
</template>
<script setup>
// eslint-disable-next-line no-unused-vars
const props = defineProps({
  todo: {
    type: Object,
    required: true
  },
  changeTodo: {
    type: Function,
    required: true
  },
  deleteTodo: {
    type: Function,
    required: true
  }
})
</script>
<style></style>
