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
        <Todo :todoItems="todoItems" :item="item" @removeItem="(id) => removeItem(id)" @renameItem="(id, message) => renameItem(id, message)" />
      </li>
    </ul>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Todo from './Todo.vue'
import { TodoItem } from './item'
const description = ref<string>('')

const todoItems = ref<TodoItem[]>([])

const addItem = () => {
  todoItems.value = [
    ...todoItems.value,
    {
      id: Date.now().toString(),
      description: description.value,      
    }
  ]

  description.value = ''
}

const removeItem = (id: string) => {
  todoItems.value = todoItems.value.filter((item) => item.id !== id)
};

const renameItem = (id: string, description: string) => {
  todoItems.value = todoItems.value.map((item) => {
    if (item.id === id) {
      return { id, description };
    } else {
      return item;
    }
  })
}

</script>

<style scoped>

</style>
