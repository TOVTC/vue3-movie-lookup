<script setup>
    import MediaService from '../services/MediaService.js'
    import MovieList from '../components/MovieList.vue'
    import { onMounted, ref } from 'vue'

    const props = defineProps({
        movieName: {
            type: String,
            required: true
        }
    })
    const movies = ref([])
    onMounted(async () => {
        let response = await MediaService.getResults(props.movieName)
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
        <h2>Results for "Search":</h2>
        <MovieList :movies="movies"/>
    </main>
</template>