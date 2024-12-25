<template>
  <div
    class="book-card flex flex-col bg-pink-50 border border-pink-200 rounded-lg shadow-md p-4 hover:shadow-lg transition-shadow duration-300"
  >
    <img :src="book.imageSrc" alt="Book cover" class="rounded-t-lg w-full h-48 object-cover mb-4" />
    <h3 class="text-lg font-bold text-pink-700 mb-2">{{ book.title }}</h3>
    <p class="text-pink-600 mb-1"><strong>Author:</strong> {{ book.author }}</p>
    <p class="text-pink-600 mb-4 h-20 overflow-hidden">{{ book.description }}</p>
    <button
      @click="deleteBook"
      class="self-start bg-pink-500 text-white px-4 py-2 rounded-lg hover:bg-pink-600 transition-colors duration-300"
    >
      Delete
    </button>
  </div>
</template>

<script setup>
const emit = defineEmits(['delete-book'])
const props = defineProps({
  book: Object,
})

function deleteBook() {
  emit('delete-book')
}
</script>
