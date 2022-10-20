<template>
  <div>
    <h1>{{ msg }}</h1>
    <button @click="count++">+{{ count }}</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const msg = "HelloWorld";
const count = ref(10);
</script>

<style scoped></style>
