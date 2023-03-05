<script setup lang="ts">
import { ref, type Ref } from 'vue'
import AddForm from '@/components/AddForm.vue'
import Modal from '@/components/Modal.vue'
import Todo from '@/components/Todo.vue'
import type { TodoType } from '@/types'

const todos = [
  {
    id: 1,
    title: 'Learn Vue',
    done: false,
    description: 'Learn Vue 3'
  },
  {
    id: 2,
    title: 'Learn React',
    done: false,
    description: 'Learn React 17'
  },
  {
    id: 3,
    title: 'Learn Angular',
    done: true,
    description: 'Learn Angular 12'
  }
]

const todosRef: Ref<TodoType[]> = ref(todos)

const isModalOpen = ref(false)

const toggleModal = () => {
  isModalOpen.value = !isModalOpen.value
}

const addTodo = (todo: TodoType) => {
  todosRef.value.push(todo)
}

const deleteTodo = (id: number) => {
  todosRef.value = todosRef.value.filter((todo) => todo.id !== id)
}
</script>

<template>
  <div class="mainDiv">
    <AddForm :toggleModal="toggleModal" />
    <Todo v-for="todo in todosRef" :key="todo.id" :todo="todo" :deleteTodo="deleteTodo" />
    <Modal v-if="isModalOpen" :toggleModal="toggleModal" :addTodo="addTodo" />
  </div>
</template>

<style scoped>
.mainDiv {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 0px;
  gap: 10px;
}
</style>
