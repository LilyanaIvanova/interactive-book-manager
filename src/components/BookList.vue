<template>
  <div class="book-list grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 p-6 bg-pink-50">
    <BookCard
      v-for="(book, index) in books"
      :key="index"
      :book="book"
      @delete-book="handleDelete(index)"
      class="shadow-md rounded-lg overflow-hidden border border-pink-200 bg-white hover:shadow-lg transition-shadow duration-300"
    />
  </div>
</template>

<script setup>
import BookCard from './BookCard.vue'

const emit = defineEmits(['delete-book'])
const props = defineProps({
  books: Array,
})

function handleDelete(index) {
  emit('delete-book', index)
}
</script>

<style scoped>
.book-list {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
