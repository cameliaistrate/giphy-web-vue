<template>
  <div>
    <form @submit.prevent="emit('search', searchQuery)">
      <div class="flex gap-2 items-center">
        <label for="input-text">Search GIFs:</label>
        <input
          type="text"
          id="input-text"
          v-model="searchQuery"
          class="rounded-md h-8 border-0 px-3.5 py-1.5 text-sm text-gray-900 shadow-sm ring-1 ring-inset ring-cyan-300 focus:ring-2 focus:ring-inset focus-ring-cyan-400"
        />
        <button
          type="submit"
          class="ml-2 px-3.5 py-1.5 rounded-md bg-cyan-400 text-sm font-semibold text-white shadow-sm hover:bg-cyan-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-cyan-600"
        >
          Search
        </button>
      </div>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const emit = defineEmits<{
  (e: 'search', value: string): void
}>()
const searchQuery = ref('xena') // default search query - why? cause she's awesome

onMounted(() => {
  emit('search', searchQuery.value)
})
</script>
