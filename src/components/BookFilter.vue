<template>
  <div class="flex justify-center p-4">
    <input
      v-model="filterText"
      @input="updateFilter"
      placeholder="Filter by title or author"
      class="w-full max-w-lg p-3 rounded-lg border border-pink-200 bg-pink-50 text-pink-700 placeholder-pink-400 shadow-sm focus:outline-none focus:ring focus:ring-pink-300 focus:border-pink-400"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
const emit = defineEmits(['filter-books'])
const filterText = ref('')

// Emit filter text on change
function updateFilter() {
  emit('filter-books', filterText.value)
}
</script>
