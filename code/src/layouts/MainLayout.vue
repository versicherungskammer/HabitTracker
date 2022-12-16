<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title> Einkaufsliste </q-toolbar-title>
        <q-btn flat icon="visibility" @click="toggleDarkMode"></q-btn>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { useQuasar } from "quasar";
const $q = useQuasar();

const toggleDarkMode = () => {
  $q.dark.toggle();
};
</script>
<style></style>
