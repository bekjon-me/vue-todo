<template>
  <div class="backdrop" @click.self="toggleModal">
    <form @submit.prevent="toggleModal" class="modal">
      <label>Title</label>
      <input ref="input" required type="text" v-model="title" />
      <label>Description</label>
      <textarea v-model="description"></textarea>

      <button @click="addTodoModal" type="submit">Add</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import type { TodoType } from '@/types'
import { ref, onMounted } from 'vue'
const { toggleModal, addTodo } = defineProps<{
  toggleModal: () => void
  addTodo: (todo: TodoType) => void
}>()

const input = ref()

const title = ref('')
const description = ref('')

const addTodoModal = () => {
  addTodo({
    id: Math.floor(Math.random() * 1000),
    title: title.value,
    description: description.value,
    done: false
  })
  toggleModal()
}

onMounted(() => {
  input.value.focus()
})
</script>

<style scoped>
.backdrop {
  width: 100vw;
  height: 100%;
  position: fixed;
  top: 0;
  backdrop-filter: blur(2px);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  width: 60vh;
  background-color: #fff;
  padding: 20px;
  border-radius: 14px;
  box-shadow: 2px 2px 10px 0px rgba(0, 0, 0, 0.75);
  display: flex;
  flex-direction: column;
  row-gap: 10px;
}

label {
  font-size: 20px;
  color: #000;
  font-family: ubuntu, sans-serif;
}

input,
textarea {
  padding: 6px;
  border: none;
  background-color: #eee;
  border-radius: 8px;
  resize: none;
}

button {
  width: 100%;
  background-color: green;
  padding: 10px;
  border-radius: 15px;
  border: none;
}
</style>
