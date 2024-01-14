<script setup lang="ts">
import PersonPostForm from './PersonPostForm.vue'
import PersonList from './PersonList.vue'
import { ref } from 'vue'
import type { Ref } from 'vue'

export type Person = {
  id: number
  name: string
  age: number
}

const persons: Ref<Person[]> = ref([
  { id: 1, name: 'John', age: 20 },
  { id: 2, name: 'Bob', age: 25 }
])

/**
 * Register Person
 *
 * @param {Person} person Person for Register
 */
const onRegister = (person: Person) => {
  persons.value.push(person)
}

/**
 * Delete Person
 * @param {number} id ID
 */
const onDelete = (id: number) => {
  persons.value = persons.value.filter((person) => person.id !== id)
}
</script>

<template>
  <div class="container">
    <h1>Title</h1>
    <PersonPostForm @register="onRegister" />
    <div class="list-container">
      <ul>
        <PersonList :persons="persons" @delete="onDelete" />
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
