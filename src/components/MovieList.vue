<script setup>

const props = defineProps({
    movies: {
        type: Array,
        required: true
    }
})
</script>

<template>
    <ul>
        <RouterLink :to="{ name: 'movie-details' }" v-for="movie in movies" :key="movie.id">
            <li>{{ movie.title }} ({{ movie.year }})</li>
        </RouterLink>
    </ul>
</template>