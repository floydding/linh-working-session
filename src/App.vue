<template>
  <h1>Linh's TODO App</h1>
  <div>
    <label for="item-input">item description</label>
    <input id="item-input" type="text" v-model="description" />
    <button @click="addItem">Add item</button>
  </div>
  <div>
    <ul>
      <li v-for="(item, index) in todoItems" :key="index">
        {{ item }}
      </li>
    </ul>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const description = ref<string>('')

const todoItems = ref<string[]>([])

const addItem = () => {
  todoItems.value = [
    ...todoItems.value,
    description.value
  ]

  description.value = ''
}


</script>

<style scoped>

</style>
