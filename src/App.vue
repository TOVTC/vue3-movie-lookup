<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="page-container">
      <header>
            <RouterLink :to="{ name: 'home' }"><h1>Movie Lookup</h1></RouterLink>
          <nav>
            <RouterLink :to="{ name: 'trending' }">Trending</RouterLink> |
            <RouterLink :to="{ name: 'popular' }">Popular</RouterLink> |
            <RouterLink :to="{ name: 'top-rated' }">Top Rated</RouterLink> |
            <RouterLink :to="{ name: 'now-playing' }">Now Playing</RouterLink>
          </nav>
      </header>
      <div id="content-wrap">
        <RouterView />
      </div>
    <footer id="footer">
        <!-- <img src="@/assets/tmdb.svg" id="logo"/> -->
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
  padding-bottom: 2.5rem;
}

#footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 2.5rem;
}
</style>
