<template>
  <h1>Linh's TODO App</h1>
  <div>
    <label for="item-input">item description</label>
    <input id="item-input" type="text" v-model="description" />
    <button @click="addItem">Add item</button>
  </div>
  <div>
    <ul>
      <li v-for="item in todoItems" :key="item.id">
        {{ item.description }}
        <button @click="removeItem(item.id)">Remove item</button>
        <input :value="message" @input=renameItem(item.id, message) placeholder="Rename item here" />
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const description = ref<string>('')

type TodoItem = {
  id: string,
  description: string
}

const todoItems = ref<TodoItem[]>([])

const addItem = () => {
  todoItems.value = [
    ...todoItems.value,
    {
      id: new Date().toISOString(),
      description: description.value
    }
  ]

  description.value = ''
}

const removeItem = (id: string) => {
  todoItems.value = todoItems.value.filter(item => item.id !== id)
}

const renameItem = (id: string, description: string) => {
  todoItems.value = todoItems.value.map(item =>
      (item.id === id) ? {id, description} : {item.id, item.description}
  )
}

</script>

<style scoped>

</style>
