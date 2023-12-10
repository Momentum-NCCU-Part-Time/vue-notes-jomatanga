<template>
  <h1>NOTED!</h1>

  <!-- Right below this is my Note Form-->
  <NoteForm />

  <NoteList />

  <!-- NOTE CONTAINER BELOW -->
  <div class="allnotes">
    <!-- This would be styled via .allnotes in CSS 
      - change display style 
      -- do all the pretty things! 
    -->
  </div>
</template>

<style scoped></style>

<script setup>
import NoteForm from "./assets/NoteForm.vue";
import NoteList from "./assets/NoteList.vue";
</script>
