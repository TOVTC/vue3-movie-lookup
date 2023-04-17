<script setup>
// import ref to create state
import { ref } from 'vue'

const movies = ref([
    {
        title: "Title 5",
        year: 2025
    },
    {
        title: "Title 4",
        year: 2024
    },
    {
        title: "Title 3",
        year: 2023
    },
    {
        title: "Title 2",
        year: 2022
    },
    {
        title: "Title 1",
        year: 2021
    }
])
</script>

<template>
    <ul>
        <RouterLink :to="{ name: 'movie-details' }" v-for="(movie, index) in movies" :key="index">
            <li>{{ movie.title }} ({{ movie.year }})</li>
        </RouterLink>
    </ul>
</template>