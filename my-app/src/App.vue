<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'

const comments = ref([])

async function getComments() {
  const { data } = await supabase.from('comments').select()
  comments.value = data
}

onMounted(() => {
  getComments()
})
</script>

<template>
  <ul>
    <li v-for="comments in comments" :key="comments.id">{{ comment.name }} {{ comment.comment }}</li>
  </ul>
</template>