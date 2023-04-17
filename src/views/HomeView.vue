<script setup>
  import { ref } from 'vue'
  const movieName = ref("Black Panther")
</script>

<template>
  <main>
    <form id="search-form">
        <label for="movie-name">Enter a movie name:</label><br/>
        <input type="text" id="search">
        <RouterLink :to="{ name: 'results', params: { movieName: movieName } }"><button type="submit">Search</button></RouterLink>
    </form>
  </main>
</template>
