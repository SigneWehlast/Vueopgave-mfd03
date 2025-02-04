<script setup>
import { ref } from 'vue';

const message = ref('Hello, vue 3!');
</script>

<template>
    <div>
        <h1>MyComponent</h1>
        <p>{{ message }}</p>
        <input v-model="message" />
    </div>
</template>

<style scoped lang="scss">
</style>