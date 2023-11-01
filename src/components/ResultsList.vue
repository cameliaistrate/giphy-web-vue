<template>
  <div class="flex flex-col gap-3">
    <span v-if="props.count && props.totalCount">
      Displaying {{ props.count }} results out of {{ props.totalCount }}</span
    >
    <div v-for="result in props.results" :key="result.id">
      <h3>{{ result.title }}</h3>
      <img :src="result.images.downsized_medium.url" alt="result.title" />
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineProps } from 'vue'

const props = defineProps({
  results: {
    type: Array as () => any[],
    required: true
  },
  count: {
    type: Number,
    required: false
  },
  totalCount: {
    type: Number,
    required: false
  }
})
</script>
