<template>
  <div class="q-pa-md" v-for="habit in habits">
    <q-card class="my-card">
      <q-card-section>
        <q-checkbox v-model="habit.ready"> </q-checkbox> {{ habit.title }}
      </q-card-section>
    </q-card>
  </div>
  <div id="addbutton">
    <q-btn
      color="white"
      text-color="black"
      label="+"
      @click="addbutton = true"
    />
    <q-dialog v-model="addbutton" persistent>
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Your Habit</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input
            dense
            v-model="habit"
            autofocus
            @keyup.enter="prompt = false"
          />
        </q-card-section>

        <q-card-actions class="text-primary">
          <q-btn flat label="Cancel" v-close-popup />
          <q-btn flat label="Add Habit" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script setup>
import { ref } from "vue";
const addbutton = ref(false);
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
