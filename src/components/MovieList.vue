<script setup>

const props = defineProps({
    movies: {
        type: Array,
        required: true
    }
})
</script>

<template>
    <ul v-if="movies.length">
        <RouterLink :to="{ name: 'movie-details' }" v-for="movie in movies" :key="movie.id">
            <li>{{ movie.title }} ({{ movie.release_date.split("-")[0] }})</li>
        </RouterLink>
    </ul>
</template>