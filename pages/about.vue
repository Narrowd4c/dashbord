<template>
  <div class="container">
    <h1 class="p-2 text-lime-500 hover:text-red-400">{{ title }}</h1>
  </div>
</template>
<script setup>
import { ref } from "vue";
const title = ref < string > ("About Page");

</script>
<style></style>
