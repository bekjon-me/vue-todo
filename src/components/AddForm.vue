<template>
  <form class="addForm">
    <button @click.prevent="toggleModal" type="submit">Add todo</button>
  </form>
</template>

<script setup lang="ts">
defineProps<{
  toggleModal: () => void
}>()
</script>

<style scoped>
.addForm {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  gap: 10px;
}

.addForm button {
  background: #20eeb0;
  border-radius: 5px;
  border: none;
  color: #fff;
  padding: 10px 20px;
  font-size: 30px;
  cursor: pointer;
}
</style>
