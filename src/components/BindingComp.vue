<script setup>
import { ref } from 'vue';

const isEditable = ref(true);
</script>

<template>
    {{ isEditable }}
    <button @click="isEditable = !isEditable">
        {{ isEditable ? 'Gør ikke redigerbar' : 'Gør redigerbar' }}
    </button>
    <p :contenteditable="isEditable">Dette er en tekst, som kan redigeres</p>

</template>

<style scoped lang="scss">
</style>