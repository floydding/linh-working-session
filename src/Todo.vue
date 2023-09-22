<template>
    <div>
        <span> {{ props.item.description }} </span>
        <button @click="emits('removeItem', item.id)">Remove item</button>
        <input v-model="message" placeholder="Rename item here" v-on:blur="() => {
            emits('renameItem', item.id, message);
            message = '';
        }"/>
    </div>
</template>

<script setup lang="ts">

import { ref } from 'vue';
import { TodoItem } from './item'

const props = defineProps<{
    item: TodoItem,
}>()

const emits = defineEmits<{
    (e: 'removeItem', id: string): void
    (e: 'renameItem', id: string, message: string): void
}>()

const message = ref("");

</script>
