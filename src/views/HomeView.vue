<template>
  <main class="container my-6 mx-auto">
    <div class="w-full flex flex-col gap-6 mx-auto">
      <h1 class="text-xl font-bold">GIF Search</h1>
      <SearchBar @search="runSearch" />
      <ResultsList
        :results="results"
        :count="results?.pagination?.count"
        :total-count="results?.pagination?.total_count"
      />
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { type Ref } from 'vue'
import axios from 'axios'
import SearchBar from '@/components/SearchBar.vue'
import ResultsList from '@/components/ResultsList.vue'

const pagination = ref({
  limit: 3,
  offset: 0
})

const results: Ref<any> = ref([])
function runSearch(e: string) {
  const url = `https://api.giphy.com/v1/gifs/search?api_key=${
    import.meta.env.VITE_GIPHY_KEY
  }&q=${e}&limit=${pagination.value.limit}&offset=${pagination.value.offset}&rating=g&lang=en`

  axios.get(url).then((res) => {
    results.value = res.data.data
  })
}
</script>
