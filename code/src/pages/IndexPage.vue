<template>
  <q-page>
    <q-checkbox v-model="val" />
    {{ counter }}
  </q-page>
  <q-card class="my-card">
    <q-card-section>
      {{ counter }}
    </q-card-section>
  </q-card>
</template>

<script setup>
import { ref } from "vue";

const name = ref(false);
</script>
<style>
#wort {
  width: 20%;
}
</style>
