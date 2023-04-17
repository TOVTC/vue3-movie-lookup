<script setup>
    import MovieList from '../components/MovieList.vue'
    // import ref to create state
    import { ref } from 'vue'

    const movies = ref([
        {
            title: "Title 5",
            year: 2025,
            id: 5
        },
        {
            title: "Title 4",
            year: 2024,
            id: 4
        },
        {
            title: "Title 3",
            year: 2023,
            id: 3
        },
        {
            title: "Title 2",
            year: 2022,
            id: 2
        },
        {
            title: "Title 1",
            year: 2021,
            id: 1
        }
    ])
</script>

<template>
    <main>
        <h2>Results for "Search":</h2>
        <MovieList :movies="movies"/>
    </main>
</template>