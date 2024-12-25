<template>
  <div class="min-h-screen bg-pink-50 flex flex-col items-center py-8">
    <h1 class="text-3xl font-bold text-pink-700 mb-6">My Book Library</h1>
    <AddBook @add-book="addBook" class="w-full max-w-3xl mb-6" />
    <BookFilter @filter-books="filterBooks" class="w-full max-w-3xl mb-6" />
    <BookList :books="filteredBooks" @delete-book="deleteBook" class="w-full max-w-3xl" />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import AddBook from './components/AddBook.vue'
import BookList from './components/BookList.vue'
import BookFilter from './components/BookFilter.vue'

// Store all books
const books = ref([])
// Filter state
const filterText = ref('')

// Computed value for filtered books
const filteredBooks = computed(() => {
  return books.value.filter(
    (book) =>
      book.title.toLowerCase().includes(filterText.value.toLowerCase()) ||
      book.author.toLowerCase().includes(filterText.value.toLowerCase()),
  )
})

// Function to add a new book
function addBook(newBook) {
  books.value.push(newBook)
}

// Function to delete a book by index
function deleteBook(index) {
  books.value.splice(index, 1)
}

// Update filter text
function filterBooks(text) {
  filterText.value = text
}
</script>
