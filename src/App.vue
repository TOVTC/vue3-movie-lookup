<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="page-container">
      <header class="flex flex-wrap justify-between items-center h-20 p-5 bg-teal-200">
            <RouterLink :to="{ name: 'home' }"><h1 class="text-2xl font-bold">Movie Lookup</h1></RouterLink>
          <nav class="p-1">
            <RouterLink :to="{ name: 'trending' }" class="hover:text-cyan-500">Trending</RouterLink> |
            <RouterLink :to="{ name: 'popular' }" class="hover:text-cyan-500">Popular</RouterLink> |
            <RouterLink :to="{ name: 'top-rated' }" class="hover:text-cyan-500">Top Rated</RouterLink> |
            <RouterLink :to="{ name: 'now-playing' }" class="hover:text-cyan-500">Now Playing</RouterLink>
          </nav>
      </header>
      <div id="content-wrap" class="m-5">
        <RouterView />
      </div>
    <footer id="footer" class="flex flex-wrap justify-between items-center p-3 bg-teal-200">
        <img src="@/assets/tmdb.svg" id="logo" class="max-w-xs"/>
        <p class="text-sm">This product uses the TMDB API but is not endorsed or certified by TMDB</p>
    </footer>
  </div>
</template>

<style scoped>
#page-container {
  position: relative;
  min-height: 100vh;
}

#content-wrap {
  padding-bottom: 4.5rem;
}

#footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 4.5rem;
}

@media (max-width: 1250px) {
    header, footer {
        justify-content: center;
        padding: 0.5rem;
    }
    footer p {
      display: none;
    }
}
</style>
