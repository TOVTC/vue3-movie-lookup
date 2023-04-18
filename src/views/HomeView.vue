<script setup>
  import { ref } from 'vue'
  import router from '../router'
  const movieName = ref(null)

  const search = () => {
    if (!movieName.value) {
      alert("please enter a search term")
      return
    }
    router.push({ name: 'results', params: { movieName: movieName.value } })
  }
</script>

<template>
  <main class="flex justify-center items-center">
    <form id="search-form" @submit.prevent="search">
        <label for="movie-name">Enter a movie name:</label><br/>
        <input type="text" id="search" v-model="movieName" class="border-2">
        <!-- <RouterLink :to="{ name: 'results', params: { movieName: movieName } }"><button type="submit">Search</button></RouterLink> -->
        <button type="submit" class="px-3">Search</button>
    </form>
  </main>
</template>
