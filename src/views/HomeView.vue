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
  <main class="flex justify-center p-10">
    <form @submit.prevent="search">
        <label for="movie-name" class="my-2">Enter a movie name:</label><br/>
        <input type="text" name="movie-name" v-model="movieName" class="border-2">
        <!-- <RouterLink :to="{ name: 'results', params: { movieName: movieName } }"><button type="submit">Search</button></RouterLink> -->
        <button type="submit" class="border-2 mx-1 px-2">Search</button>
    </form>
  </main>
</template>
