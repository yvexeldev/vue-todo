<template>
  <div class="flex flex-col lg:gap-5 gap-3">
    <div>
      <h1 class="lg:text-4xl text-2xl font-black lg:mb-4 mb-2 text-white flex items-center">
        <img src="../../assets/icons/emoji1.svg" class="lg:block hidden" alt="" />
        <span>Tasks-[{{ todos.filter((todo) => !todo.isCompleted).length }}]</span>
      </h1>
      <div class="bg-gray-800 flex flex-col lg:gap-8 gap-4 lg:p-5 p-2 rounded-md">
        <div
          class="flex items-center gap-2"
          v-show="todos.filter((todo) => !todo.isCompleted).length == 0"
        >
          <img src="../../assets/icons/warning.svg" class="lg:block hidden" alt="" />
          <h1 class="lg:text-2xl text-xl font-bold text-orange-600">Empty todo!</h1>
        </div>
        <div v-for="todo in todos.filter((todo) => !todo.isCompleted)" :key="todo.id">
          <TodoItem :todo="todo" :changeTodo="changeTodo" :deleteTodo="deleteTodo" />
        </div>
      </div>
    </div>

    <div>
      <h1 class="lg:text-4xl text-2xl font-black lg:mb-4 mb-2 text-white flex items-center gap-2">
        <img src="../../assets/icons/checkbox.svg" class="hidden lg:block" alt="" />
        <span>Completed-[{{ todos.filter((todo) => todo.isCompleted).length }}]</span>
      </h1>
      <div class="bg-gray-800 flex flex-col lg:gap-8 gap-4 lg:p-5 p-2 rounded-md">
        <div
          class="flex items-center gap-2"
          v-show="todos.filter((todo) => todo.isCompleted).length == 0"
        >
          <img class="lg:block hidden" src="../../assets/icons/warning.svg" alt="" />
          <h1 class="lg:text-2xl text-xl font-bold text-orange-600">Empty completed todos!</h1>
        </div>
        <div v-for="todo in todos.filter((todo) => todo.isCompleted)" :key="todo.id">
          <TodoItem :todo="todo" :changeTodo="changeTodo" :deleteTodo="deleteTodo" />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import TodoItem from './TodoItem.vue'

// eslint-disable-next-line no-unused-vars
const props = defineProps({
  todos: {
    type: Array,
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
