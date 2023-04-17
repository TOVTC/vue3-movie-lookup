<script setup>
    import MovieList from '../components/MovieList.vue'
    import { onMounted, ref, computed } from 'vue'

    const movies = ref([])
    const film = ref({
                "adult": false,
                "backdrop_path": "/xDMIl84Qo5Tsu62c9DGWhmPI67A.jpg",
                "belongs_to_collection": {
                "id": 529892,
                "name": "Black Panther Collection",
                "poster_path": "/qT1JPO6IltC2B39QAriAg7SelMx.jpg",
                "backdrop_path": "/yzVxUMYGKjK3GgmVI2BhmbuL9UY.jpg"
                },
                "budget": 250000000,
                "genres": [
                {
                "id": 28,
                "name": "Action"
                },
                {
                "id": 12,
                "name": "Adventure"
                },
                {
                "id": 878,
                "name": "Science Fiction"
                }
                ],
                "homepage": "https://wakandaforevertickets.com",
                "id": 505642,
                "imdb_id": "tt9114286",
                "original_language": "en",
                "original_title": "Black Panther: Wakanda Forever",
                "overview": "Queen Ramonda, Shuri, M’Baku, Okoye and the Dora Milaje fight to protect their nation from intervening world powers in the wake of King T’Challa’s death.  As the Wakandans strive to embrace their next chapter, the heroes must band together with the help of War Dog Nakia and Everett Ross and forge a new path for the kingdom of Wakanda.",
                "popularity": 1246.715,
                "poster_path": "/sv1xJUazXeYqALzczSZ3O6nkH75.jpg",
                "production_companies": [
                {
                "id": 420,
                "logo_path": "/hUzeosd33nzE5MCNsZxCGEKTXaQ.png",
                "name": "Marvel Studios",
                "origin_country": "US"
                }
                ],
                "production_countries": [
                {
                "iso_3166_1": "US",
                "name": "United States of America"
                }
                ],
                "release_date": "2022-11-09",
                "revenue": 859102154,
                "runtime": 162,
                "spoken_languages": [
                {
                "english_name": "English",
                "iso_639_1": "en",
                "name": "English"
                },
                {
                "english_name": "French",
                "iso_639_1": "fr",
                "name": "Français"
                },
                {
                "english_name": "Haitian; Haitian Creole",
                "iso_639_1": "ht",
                "name": ""
                },
                {
                "english_name": "Spanish",
                "iso_639_1": "es",
                "name": "Español"
                },
                {
                "english_name": "Xhosa",
                "iso_639_1": "xh",
                "name": ""
                }
                ],
                "status": "Released",
                "tagline": "Forever.",
                "title": "Black Panther: Wakanda Forever",
                "video": false,
                "vote_average": 7.294,
                "vote_count": 4478
                },)

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
</script>

<template>
    <main>
        <section v-if="film">
            <h2>{{ film.original_title ? film.original_title : film.title }} {{ film.release_date ? `(${film.release_date.split("-")[0]})` : "" }}</h2>
            <div class="movie-details">
                <img :src="url" :alt="altText" />
                <div class="movie-details">
                    <ul>
                        <li v-if="film.tagline">{{ `"${film.tagline}"` }}</li>
                        <li v-if="film.release_date">{{ `Release Date - ${film.release_date}` }} </li>
                        <li v-if="runTime">{{`Runtime - ${runTime}` }}</li>
                        <li v-if="genres">{{ getGenres ? `Genres - ${genres}` : ""}}</li>
                        <li v-if="languages">Languages {{ film.original_language ? `(${film.original_language})` : "" }}{{ languages ? ` - ${languages}` : "" }}</li>
                        <li v-if="companies">{{ companies ? `Production Company - ${companies}` : "" }}</li>
                        <li v-if="link"><a :href="link"><span class="exception">{{ link ? link : "" }}</span></a></li>
                        <li id="description" v-if="film.overview.length">{{ film.overview ? `Synopsis: ${film.overview}` : "" }}</li>
                    </ul>
                </div>
            </div>
        </section>
        <section id="suggested">
            <div class="list" v-if="film">
                <h3>Recommended Films:</h3>
                <MovieList :movies="movies"/>
            </div>
            <div class="list" v-if="film">
                <h3>Similar Films:</h3>
                <MovieList :movies="movies"/>
            </div>
        </section>
    </main>
</template>