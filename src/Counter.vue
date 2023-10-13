<template>
    <span>Counter size: {{ todoSize }} </span>
</template>

<script setup>
import { inject, computed } from 'vue'

const todoSize = computed(inject('todoSize'))
</script>
