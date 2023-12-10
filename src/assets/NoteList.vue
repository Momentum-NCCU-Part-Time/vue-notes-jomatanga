<template>
  <h1>Noted!</h1>
  <div class="newNote">
    <!-- <img src=""> insert my new note img/icon here--->
  </div>

  <!-- DISREGARD OLD LIST FORMAT BELOW
    <ul>
    <li v-for="note in notes">
      {{ note.title }}
      {{ note.body }}
    </li>
  </ul> -->

  <div class="noteContainer">
    <div class="noteCard" v-for="note in notes">
      <p class="noteTitle">{{ note.title }}</p>
      <p class="noteBody">{{ note.body }}</p>
      <button type="submit" id="editbutton">EDIT</button>
      <button @click="deleteNote()" type="submit" id="editbutton">
        DELETE
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const notes = ref([]);

const newAPI = "http://localhost:3000/notes/";

// GET REQUEST TO PULL NOTES FROM DATABASE OF NOTES //
fetch("http://localhost:3000/notes/", {
  method: "GET",
  headers: { "Content-Type": "application/json" },
})
  .then((response) => response.json())
  .then((response) => (notes.value = response));

// DELETE REQUEST //
const deleteNote = () => {
  fetch("${newAPI}/${id}", {
    method: "DELETE",
  }).then((res) => res.json());
};
</script>

function deleteNote() { location.reload();} Q: would a undo button involve
posting back to the server and then recalling by id?
