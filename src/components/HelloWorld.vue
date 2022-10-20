<template>
  <div>
    <h1>{{ msg }}</h1>
    <button @click="count++">+{{ count }}</button>
    <button><HomeView></HomeView></button>
    <button><AboutView></AboutView></button>
  </div>
</template>

<script setup lang="ts">
import HomeView from "../views/HomeView.vue";
import AboutView from "../views/AboutView.vue";

import { ref } from "vue";
const msg = "HelloWorld";
const count = ref(10);
</script>

<style scoped></style>
