<template>
    <span> {{ props.item.description }} </span>
    <button @click="removeItem(props.item.id)">Remove item</button>
    <input v-model="message" placeholder="Rename item here" v-on:blur="() => {
        renameItem(item.id, message);
        message = '';
    }"/>
</template>

<script setup lang="ts">

import { ref } from 'vue';
import { TodoItem } from './item'

const props = defineProps<{
    item: TodoItem,
    removeItem: (id: string) => void,
    renameItem: (id: string, message: string) => void,
}>()

const message = ref("");

</script>
