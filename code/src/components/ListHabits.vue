<template>
  <div class="q-pa-md" v-for="habit in habits">
    <q-card class="my-card">
      <q-card-section>
        <q-checkbox v-model="habit.ready"> </q-checkbox> {{ habit.title }}
      </q-card-section>
    </q-card>
  </div>
  <div id="addbutton">
    <q-btn color="white" text-color="black" label="+" />
  </div>
</template>

<script setup>
import { ref } from "vue";
//const addHabit = () => {
//habits.value.push({ title: "irgendwas", ready: false });
//};
const habits = ref([
  { title: "Sport machen", ready: false },
  { title: "Duschen", ready: false },
  { title: "Trinken", ready: false },
  { title: "Essen", ready: false },
]);
</script>
<style>
#addbutton {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
