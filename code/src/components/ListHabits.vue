<template>
  <div v-for="habit in habits">{{ habit.title }}, {{ habit.ready }}</div>
</template>

<script setup>
import { ref } from "vue";
const habits = ref([
  { title: "Sport machen", ready: false },
  { title: "Duschen", ready: false },
  { title: "Trinken", ready: false },
  { title: "Essen", ready: false },
]);
</script>
