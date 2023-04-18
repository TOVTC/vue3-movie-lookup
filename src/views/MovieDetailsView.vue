<script setup>
    import MovieList from '../components/MovieList.vue'
    import MediaService from '../services/MediaService.js'
    import { onMounted, ref, computed } from 'vue'

    const props = defineProps({
        id: {
            type: String,
            required: true
        }
    })
    const recommendedMovies = ref([])
    const similarMovies = ref([])
    const film = ref(null)

    const url = computed(() => {
        return `https://image.tmdb.org/t/p/original${film.value.poster_path}`
    })
    const altText = computed(() => {
        return film.value.title + " movie poster"
    })
    const runTime = computed(() => {
        let hours = Math.floor(film.value.runtime/60)
            let minutes = film.value.runtime % 60
            if (hours !== 0 && minutes !== 0) {
                return `${hours}h ${minutes}min`
            }
            return false
    })
    const genres = computed(() => {
        let genres = []
            film.value.genres.forEach(genre => {
                genres.push(genre.name)
            })
            if (genres.length) {
                return genres.join(", ")
            }
            return false
    })
    const languages = computed(() => {
        let languages = []
            film.value.spoken_languages.forEach(language => {
                languages.push(language.english_name)
            })
            if (languages.length) {
                return languages.join(", ")
            }
            return false
    })
    const companies = computed(() => {
        let companies = []
            film.value.production_companies.forEach(studio => {
                companies.push(studio.name)
            })
            if (companies.length) {
                return companies.join(", ")
            }
            return false
    })
    const link = computed(() => {
        if (!film.value.homepage || film.value.homepage === "") {
                return false
            }
            return film.value.homepage
    })

    onMounted(async () => {
        let details = await MediaService.getDetails(props.id)
        let recommended = await MediaService.getRecommended(props.id)
        let similar = await MediaService.getSimilar(props.id)
        if (!details || !recommended || !similar) {
            alert("something went wrong")
            return
        } else {
            film.value = details.data
            recommendedMovies.value = recommended.data.results
            similarMovies.value = similar.data.results
        }
    })
</script>

<template>
    <main class="p-10">
        <section v-if="film">
            <h2 class="text-2xl font-bold">{{ film.original_title ? film.original_title : film.title }} {{ film.release_date ? `(${film.release_date.split("-")[0]})` : "" }}</h2>
            <div id="movie-details" class="flex items-end">
                <img :src="url" :alt="altText"  class="max-h-96 m-3"/>
                <div class="m-3">
                    <ul>
                        <li v-if="film.tagline" class="italic mb-3">{{ `"${film.tagline}"` }}</li>
                        <li v-if="film.release_date" class="text-sm">{{ `Release Date - ${film.release_date}` }} </li>
                        <li v-if="runTime" class="text-sm">{{`Runtime - ${runTime}` }}</li>
                        <li v-if="genres" class="text-sm">{{ genres ? `Genres - ${genres}` : ""}}</li>
                        <li v-if="languages" class="text-sm">Languages {{ film.original_language ? `(${film.original_language})` : "" }}{{ languages ? ` - ${languages}` : "" }}</li>
                        <li v-if="companies" class="text-sm">{{ companies ? `Production Company - ${companies}` : "" }}</li>
                        <li v-if="link" class="text-sm hover:text-teal-500"><a :href="link"><span class="exception">{{ link ? link : "" }}</span></a></li>
                        <li v-if="film.overview.length" class="mt-3">{{ film.overview ? `Synopsis: ${film.overview}` : "" }}</li>
                    </ul>
                </div>
            </div>
        </section>
        <section class="flex flex-wrap justify-between">
            <div v-if="film" class="m-3">
                <h3 class="text-lg font-bold">Recommended Films:</h3>
                <MovieList :movies="recommendedMovies"/>
            </div>
            <div v-if="film" class="m-3">
                <h3 class="text-lg font-bold">Similar Films:</h3>
                <MovieList :movies="similarMovies"/>
            </div>
        </section>
    </main>
</template>

<style scoped>
@media (max-width: 1250px) {
    #movie-details {
        flex-wrap: wrap;
    }
}
</style>