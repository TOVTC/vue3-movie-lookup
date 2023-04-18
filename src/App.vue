<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="page-container">
      <header class="flex flex-wrap justify-between items-center h-20 p-5 bg-cyan-200">
            <RouterLink :to="{ name: 'home' }"><h1>Movie Lookup</h1></RouterLink>
          <nav>
            <RouterLink :to="{ name: 'trending' }">Trending</RouterLink> |
            <RouterLink :to="{ name: 'popular' }">Popular</RouterLink> |
            <RouterLink :to="{ name: 'top-rated' }">Top Rated</RouterLink> |
            <RouterLink :to="{ name: 'now-playing' }">Now Playing</RouterLink>
          </nav>
      </header>
      <div id="content-wrap" class="m-5">
        <RouterView />
      </div>
    <footer id="footer" class="flex flex-wrap justify-between items-center p-3 bg-cyan-200">
        <img src="@/assets/tmdb.svg" id="logo" class="max-w-xs"/>
        <p>This product uses the TMDB API but is not endorsed or certified by TMDB</p>
    </footer>
  </div>
</template>

<style scoped>
#page-container {
  position: relative;
  min-height: 100vh;
}

#content-wrap {
  padding-bottom: 4rem;
}

#footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 4rem;
}
</style>
