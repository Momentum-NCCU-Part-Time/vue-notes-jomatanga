<template>
  <form id="noteform" @submit.prevent="createNote">
    <input v-model="noteTitle" type="text" id="notetitle" placeholder="Title" />
    <input v-model="noteBody" type="text" id="notebody" placeholder="Body" />
    <button type="submit" id="savebutton" @click="reloadPage()">SAVE</button>
  </form>
</template>

<style scoped></style>

<script setup>
import { ref } from "vue";

const apiURL = "http://localhost:3000/notes/";

const newAPI = "http://localhost:3000/notes/:id";

const noteTitle = ref("");

const noteBody = ref("");

const resetNote = () => {
  (noteTitle.value = ""), (noteBody.value = "");
};

/* THE REQUEST THAT SENDS NOTES TO SERVER DATABASE */
const createNote = () => {
  const newNote = { title: noteTitle.value, body: noteBody.value };
  fetch(apiURL, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(newNote),
  })
    .then((res) => res.json())
    .then((data) => console.log());
  resetNote();
}; /*
const deleteNote = () => {
  fetch(newAPI, {
    method: "DELETE",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(deleteNote),
  })
    .then((res) => res.json())
    .then((data) => console.log());
};
*/

function reloadPage() {
  location.reload();
}
</script>
