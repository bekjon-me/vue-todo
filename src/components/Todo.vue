<template>
  <div class="main">
    <div class="left">
      <h2 :class="isDone">{{ todo.title }}</h2>
      <p :class="isDone">{{ todo.description }}</p>
    </div>
    <div class="right">
      <input type="checkbox" v-model="todo.done" />
      <div class="deleteIcon" @click="() => deleteTodo(todo.id)">
        <Delete />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { TodoType } from '@/types'
import { computed } from 'vue'
import Delete from './icons/Delete.vue'

const isDone = computed(() => {
  return todo.done ? 'done' : ''
})

const { todo, deleteTodo } = defineProps<{
  todo: TodoType
  deleteTodo: (id: number) => void
}>()
</script>

<style scoped>
.main {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px;
  width: 40%;
  min-width: 300px;
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 15px 12px;
  font-family: ubuntu, sans-serif;
}

.main .left {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  gap: 10px;
}

.main .left h2 {
  font-size: 20px;
  font-weight: 600;
  margin: 0;
}

.main .left p {
  font-size: 16px;
  font-weight: 400;
  margin: 0;
}

.main .left h2.done {
  text-decoration: line-through;
}
.main .left p.done {
  text-decoration: line-through;
}

.main .right {
  display: flex;
  align-items: flex-end;
  padding: 0px;
  gap: 10px;
}

.main .right input {
  width: 20px;
  height: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 0px;
  margin: 0px;
  cursor: pointer;
}

.main .right .deleteIcon {
  width: 20px;
  height: 20px;
  cursor: pointer;
}
</style>
