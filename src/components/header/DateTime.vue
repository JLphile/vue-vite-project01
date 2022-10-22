<template>
  <div id="clock">{{ date }}</div>
</template>

<script lang="ts" setup>
import { formateDate } from "@/utils/formatterData";
import { ref, onMounted } from "vue";
const date = ref("");
onMounted(() => {
  setInterval(() => {
    getDate();
  }, 1000);
});

const getDate = function () {
  date.value = formateDate(new Date());
};
</script>

<style scoped></style>
