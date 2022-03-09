<template>
  <div>{{ singleNews.content }}</div>
</template>

<script setup>
  import axios from 'axios'
  import { useRoute } from 'vue-router'
  import { ref } from 'vue'
  const route = useRoute()

  const singleNews = ref({})
  axios.get(`https://api.uza.uz/api/v1/posts/${route.params.id}?include=theme,tags,translations&_f=json&_l=uz`).then((res) => {
    singleNews.value = res.data
  })
</script>
