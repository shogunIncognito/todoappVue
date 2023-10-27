<script setup>
import { ref } from 'vue';
import Form from './components/Form.vue'
import Notes from './components/Notes.vue';

const notes = ref(JSON.parse(localStorage.getItem('notes')) || [])

const createNote = (note) => {
  notes.value = [...notes.value, note]
  localStorage.setItem('notes', JSON.stringify(notes.value))
}

const deleteNote = (note) => {
  if (!confirm('Delete this note?')) return
  notes.value = notes.value.filter(not => not.id !== note.id)
  localStorage.setItem('notes', JSON.stringify(notes.value))
}

const updateStatus = (note) => {
  note.done = !note.done
  localStorage.setItem('notes', JSON.stringify(notes.value))
}

</script>

<template>
  <section class="flex flex-col justify-center items-center">
    <Form @create-note="createNote"/>
    <Notes v-if="notes.length > 0" :notes="notes" @update-status="updateStatus" @delete-note="deleteNote"/>
    <h1 v-else class="mt-10 text-2xl font-mono">There's nothing yet</h1>
  </section>
</template>

<style scoped>
</style>
