<script setup>
    import MovieList from '../components/MovieList.vue'
    import MediaService from '../services/MediaService.js'
    import { onMounted, ref } from 'vue'

    const movies = ref([])
    onMounted(async () => {
        let response = await MediaService.getTopRated()
        if (!response) {
            alert("something went wrong")
            return
        } else {
            movies.value = response.data.results
        }
    })
</script>

<template>
    <main class="p-10">
        <h2 class="text-xl font-bold">Top Rated:</h2>
        <MovieList :movies="movies"/>
    </main>
</template>