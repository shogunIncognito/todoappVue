<script setup>
defineProps(['notes'])
defineEmits(['deleteNote', 'updateStatus'])
</script>

<template>
  <section class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-5 w-4/5 my-10">

    <article v-for="note in notes" class="bg-neutral-700 shadow shadow-blue-600 relative flex flex-col break-words p-3 rounded">
      <h3 class="font-bold opacity-80 mb-2 text-xl">{{ note.title }} <span> {{ note.done ? '&#x2705;' : ' &#10060;'
      }} </span></h3> 
      <p class="break-words mb-12">{{ note.description }}</p>
      <div class="self-end flex gap-2 bottom-2 right-2 absolute">
        <button @click="$emit('updateStatus', note)" class="bg-neutral-500 hover:bg-neutral-700 py-1.5 p-2 rounded">{{ note.done ? 'Done' :
          'Undone' }}</button>
        <button @click="$emit('deleteNote', note)"
          class="bg-red-600  rounded py-1.5 px-4 hover:bg-red-800">Delete</button>
      </div>
    </article>

  </section>
</template>

<style scoped></style>