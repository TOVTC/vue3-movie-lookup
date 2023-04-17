<script setup>
// import { RouterLink } from 'vue-router'
</script>

<template>
  <main>
    <form id="search-form">
        <label for="movie-name">Enter a movie name:</label><br/>
        <input type="text" id="search">
        <RouterLink :to="{ name: 'results' }"><button type="submit">Search</button></RouterLink>
    </form>
  </main>
</template>
