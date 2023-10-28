<script setup>
import { v4 as uuidv4 } from 'uuid';
const emit = defineEmits(['createNote'])

const handleSubmit = (e) => {
  e.preventDefault()
  const data = Object.fromEntries(new FormData(e.target))
  emit('createNote', { ...data, id: uuidv4(), done: false })
  e.target.reset()
}

</script>

<template>
  <form class="bg-neutral-900 mt-10 w-5/6 md:w-1/2 lg:w-1/6 p-5 rounded" @submit="handleSubmit">

    <div class="flex flex-col">
      <label>Title</label>
      <input required class="p-1 rounded outline-none text-black" name="title" type="text">
    </div>
    <div class="flex flex-col">
      <label>Description</label>
      <textarea required class="p-1 rounded outline-none text-black" name="description" type="password" />
    </div>

    <button class="bg-blue-600 rounded py-2 mt-4 px-5 hover:bg-blue-800">Add</button>
  </form>
</template>

<style scoped></style>