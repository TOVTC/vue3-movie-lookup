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
    <main class="p-10">
        <h2 class="text-xl font-bold">Results for "{{ props.movieName }}":</h2>
        <MovieList :movies="movies"/>
    </main>
</template>