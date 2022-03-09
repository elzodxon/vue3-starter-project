<template>
  <router-link v-for="(item, index) in news" :key="index" :to="`/news/${item.slug}`" class="my-8">
    <img class="h-[120px] w-[400px]" :src="item.files.thumbnails.front.src" alt="">
    <p>{{ item.title }}</p>
  </router-link>
</template>

<script setup>
  import { useSXO } from '../hooks/app'
  import { ref } from 'vue'
  import axios from 'axios'

  const { setSEO, setSMO } = useSXO()

  const news = ref([])
  axios.get('https://api.uza.uz/api/v1/posts/last?&_f=json&_l=uz').then((res) => {
    news.value = res.data
  })

  setSEO({
    title: news.value.title,
    description: news.value.description
  })
  setSMO({ title: 'Home page title after server fetch' })

</script>
