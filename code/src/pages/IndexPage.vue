<template>
  <div>
    <ListHabits v-if="habits"> </ListHabits>
    <div v-if="!habits"></div>
  </div>
</template>

<script setup>
import ListHabits from "src/components/ListHabits.vue";
import { ref } from "vue";
const habits = ref(true);
</script>
<style></style>
