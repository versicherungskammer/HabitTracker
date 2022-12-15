<template>
  <div class="q-pa-md" v-for="(habit, index) in habits" :key="habit.id">
    <q-card class="my-card" :id="habit.id" ref="card">
      <q-card-section>
        <q-checkbox
          id="checkbox"
          v-model="habit.ready"
          @click="changeToTransparent(habit)"
        >
        </q-checkbox>
        {{ habit.title }}

        <q-btn-dropdown flat class="more" color="black" icon="more_horiz">
          <q-list>
            <q-item clickable v-close-popup @click="deletehabit(index)">
              <q-item-section>
                <q-item-label>Löschen</q-item-label>
              </q-item-section>
            </q-item>

            <q-item clickable v-close-popup @click="edithabitbutton(index)">
              <q-item-section>
                <q-item-label>Bearbeiten</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-btn-dropdown>
      </q-card-section>
    </q-card>
    <div>
      <q-dialog v-model="editbutton" persistent>
        <q-card style="min-width: 350px">
          <q-card-section>
            <div class="text-h6">Your Habit</div>
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-input
              dense
              v-model="habittitle2"
              autofocus
              @keyup.enter="prompt = false"
            ></q-input>
          </q-card-section>

          <q-card-actions class="text-primary">
            <q-btn flat label="Cancel" v-close-popup />
            <q-btn
              flat
              label="Edit Habit"
              v-close-popup
              @click="edithabit(habit.id)"
            />
          </q-card-actions>
        </q-card>
      </q-dialog>
    </div>
  </div>
  <div class="button">
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
            v-model="habittitle"
            autofocus
            @keyup.enter="prompt = false"
          />
        </q-card-section>

        <q-card-actions class="text-primary">
          <q-btn flat label="Cancel" v-close-popup />
          <q-btn flat label="Add Habit" v-close-popup @click="addHabit" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script setup>
import { ref } from "vue";
const addbutton = ref(false);
const editbutton = ref(false);
const habits = ref([]);
const habittitle = ref();
const habittitle2 = ref();
let counter = 0;
let idtoedit = 0;
const card = ref();

const addHabit = () => {
  habits.value.push({ id: counter++, title: habittitle.value, ready: false });
  savetolocalstorage();
  habittitle.value = "";
};

const getlocalstorage = () => {
  if (localStorage.getItem("myhabits") != null) {
    habits.value = JSON.parse(localStorage.getItem("myhabits"));
  }
};

getlocalstorage();

const savetolocalstorage = () => {
  localStorage.setItem("myhabits", JSON.stringify(habits.value));
};

const changeToTransparent = (habit) => {
  if (habit.ready) {
    document.getElementById(habit.id).style.backgroundColor =
      "rgba(47,87,47,0.25)";
  } else {
    document.getElementById(habit.id).style.backgroundColor = "white";
  }
};

const edithabitbutton = (id) => {
  editbutton.value = true;
  idtoedit = id;
};

const edithabit = () => {
  habits.value.splice(idtoedit, 1, {
    id: idtoedit,
    title: habittitle2.value,
    ready: false,
  });
  habittitle2.value = "";
  savetolocalstorage();
};

const deletehabit = (id) => {
  habits.value.splice(id, 1);
  console.log(id);
  savetolocalstorage();
};
</script>
<style>
.button {
  display: flex;
  justify-content: center;
  align-items: center;
}

.more {
  background-color: transparent;
  position: absolute;
  right: 1%;
}
</style>
