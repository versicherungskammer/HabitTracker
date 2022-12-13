<template>
  <div>
    <ListHabits v-if="habits"> </ListHabits>
    <div v-if="!habits">hallo</div>
  </div>
</template>

<script setup>
import ListHabits from "src/components/ListHabits.vue";
import { ref } from "vue";
const habits = ref(true);
</script>
<style>
#wort {
  width: 20%;
}
</style>
