<template>
  <div>
    <h1>{{ msg }}</h1>
    <HelloWorld />
  </div>
</template>

<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
const msg = "Hello App";
</script>

<style scoped></style>
