<template>
  <form
    @submit.prevent="handleSubmit"
    class="bg-pink-50 border border-pink-200 rounded-lg shadow-md p-6 max-w-lg mx-auto flex flex-col gap-4"
  >
    <input
      v-model="title"
      placeholder="Title"
      required
      class="p-3 border border-pink-300 rounded-lg bg-white focus:outline-none focus:ring focus:ring-pink-300 focus:border-pink-400"
    />
    <input
      v-model="author"
      placeholder="Author"
      required
      class="p-3 border border-pink-300 rounded-lg bg-white focus:outline-none focus:ring focus:ring-pink-300 focus:border-pink-400"
    />
    <input
      v-model="imageSrc"
      placeholder="Image URL"
      required
      class="p-3 border border-pink-300 rounded-lg bg-white focus:outline-none focus:ring focus:ring-pink-300 focus:border-pink-400"
    />
    <textarea
      v-model="description"
      placeholder="Description"
      class="p-3 border border-pink-300 rounded-lg bg-white focus:outline-none focus:ring focus:ring-pink-300 focus:border-pink-400"
    ></textarea>
    <button
      type="submit"
      class="bg-pink-500 text-white px-4 py-2 rounded-lg hover:bg-pink-600 transition-colors duration-300"
    >
      Add Book
    </button>
  </form>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['add-book'])

const title = ref('')
const author = ref('')
const imageSrc = ref('')
const description = ref('')

function handleSubmit() {
  // Gather data into an object
  emit('add-book', {
    title: title.value,
    author: author.value,
    imageSrc: imageSrc.value,
    description: description.value,
  })

  // Clear form fields
  title.value = ''
  author.value = ''
  imageSrc.value = ''
  description.value = ''
}
</script>
