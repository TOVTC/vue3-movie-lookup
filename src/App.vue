<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div id="page-container">
      <header>
            <RouterLink to="/"><h1>Movie Lookup</h1></RouterLink>
          <nav>
            <RouterLink to="/trending">Trending</RouterLink> |
            <RouterLink to="/popular">Popular</RouterLink> |
            <RouterLink to="/top-rated">Top Rated</RouterLink> |
            <RouterLink to="/now-playing">Now Playing</RouterLink>
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
/* header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
} */

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

/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
} */
</style>
