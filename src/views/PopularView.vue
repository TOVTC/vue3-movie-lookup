<script setup>
    import MovieList from '../components/MovieList.vue'
    import MediaService from '../services/MediaService.js'
    import { onMounted, ref } from 'vue'

    const movies = ref([])
    onMounted( async () => {
        let response = await MediaService.getPopular()
        if (!response) {
            alert("something went wrong")
            return
        } else {
            movies.value = response.data.results
        }
    })
</script>

<template>
    <main>
        <h2>Popular:</h2>
        <MovieList :movies="movies"/>
    </main>
</template>