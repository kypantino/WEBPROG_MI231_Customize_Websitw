<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'

const countries = ref([])

async function getComments() {
  const { data } = await supabase.from('comments').select()
  commentss.value = data
}

onMounted(() => {
  getComments()
})
</script>

<template>
  <ul>
    <li v-for="comments in comments" :key="comments.id">{{ comment.name }} </li>
  </ul>
</template>