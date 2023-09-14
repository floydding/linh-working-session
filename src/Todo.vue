<template>
    <span> {{ props.item.description }} </span>
    <button @click="$emit('removeItem', item.id)">Remove item</button>
    <input v-model="message" placeholder="Rename item here" v-on:blur="() => {
        $emit('renameItem', item.id, message);
        message = '';
    }"/>
</template>

<script setup lang="ts">

import { ref } from 'vue';
import { TodoItem } from './item'

const props = defineProps<{
    item: TodoItem,
}>()

const message = ref("");

</script>
