<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title> Shopping List </q-toolbar-title>
        <q-btn flat icon="visibility" @click="toggleDarkMode"></q-btn>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { LocalStorage, useQuasar } from "quasar";
const $q = useQuasar();

const toggleDarkMode = () => {
  $q.dark.toggle();
  let darkmode = $q.dark.isActive;
  localStorage.setItem("darkmode", darkmode);
};

const getDarkmode = () => {
  if (localStorage.getItem("darkmode") === "true") {
    $q.dark.set(true);
  }
};

getDarkmode();
</script>
<style></style>
