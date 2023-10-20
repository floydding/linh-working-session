<template>
    <span>Counter size: {{ todoSize }} </span>
</template>

<script setup>
import { inject } from 'vue'

const todoSize = inject('todoSize')
</script>
