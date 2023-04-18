<script setup>

const props = defineProps({
    movies: {
        type: Array,
        required: true
    }
})
</script>

<template>
    <ul v-if="movies.length" class="m-3">
        <RouterLink :to="{ name: 'movie-details', params: {id: movie.id}}" v-for="movie in movies" :key="movie.id">
            <li>{{ movie.title }} {{ movie.release_date ? `(${movie.release_date.split("-")[0]})` : "" }}</li>
        </RouterLink>
    </ul>
    <ul v-else class="m-3">
        <li>No movies of this category to display at this time</li>
    </ul>
</template>