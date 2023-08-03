<template>
  <Layout>
    <HeaderView />
    <TodoList :todos="todos" :changeTodo="changeTodo" :deleteTodo="deleteTodo" />
    <TodoForm :saveTodo="saveTodo" />
  </Layout>
  <!-- <TailwindIndicator /> -->
</template>

<script setup>
import { useStorage } from '@vueuse/core'
import TodoList from './components/todo/TodoList.vue'
import Layout from './views/LayoutView.vue'
import HeaderView from './views/HeaderView.vue'
// import TailwindIndicator from './providers/TailwindIndicator.vue'
import TodoForm from './components/todo/TodoForm.vue'

const todos = useStorage('todos', [])

const changeTodo = (todo) => {
  const updatedTodos = todos.value.map((t) => {
    if (t.id === todo.id) {
      return { ...t, isCompleted: !t.isCompleted }
    }
    return t
  })
  todos.value = updatedTodos
}

const saveTodo = (todoName) => {
  if (!todoName) {
    alert('Todo name is required!')
    return
  }
  const newTodo = {
    title: todoName,
    isCompleted: false,
    id: Date.now()
  }

  todos.value.push(newTodo)

  todoName = ''
}

const deleteTodo = (todo) => {
  todos.value = todos.value.filter((t) => t.id !== todo.id)
}
</script>

<style></style>
