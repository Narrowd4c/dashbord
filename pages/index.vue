<template>
    <div class="container">
        <h1 class="text-lime-500 p-2">{{ title }}</h1>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const title = ref<string>('Home Page')

</script>
<style>
</style>