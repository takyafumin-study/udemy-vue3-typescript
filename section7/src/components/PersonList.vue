<script setup lang="ts">
import { defineProps } from 'vue'
import type { Person } from './Persons.vue'

type Props = {
  persons: Person[]
}

defineProps<Props>()

const emit = defineEmits(['delete'])

const onDelete = (id: number) => {
  emit('delete', id)
}
</script>

<template>
  <li v-for="person in persons" :key="person.id" class="person-list">
    <span>{{ person.name }}</span>
    <span>{{ person.age }}</span>
    <button @click="() => onDelete(person.id)">
      <span>delete</span>
    </button>
  </li>
</template>

<style scoped>
.person-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 20px;
  font-weight: bold;
  display: flex;
  justify-content: space-between;
  background-color: rgb(228, 201, 133);
  padding: 8px 20px;
  width: 300px;
}
</style>
