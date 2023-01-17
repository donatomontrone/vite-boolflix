<template>
    <!-- Eseguire in v for sulla singola card -->
    <SingleMovieComponent v-for="movie in store.movies" :movieLanguage="movie.original_language"
        :movieTitle="movie.title" :movieOriginalTitle="movie.original_title" :moviePoster="movie.poster_path"
        :movieVote="Math.ceil(movie.vote_average / 2)" :movieOverview="movie.overview" />
</template>
<script>
import { store } from '../../store.js';
import SingleMovieComponent from './SingleMovieComponent.vue';
export default {
    name: 'MovieListComponent',
    components: {
        SingleMovieComponent,
    },
    data() {
        return {
            store,
        }
    },
}
</script>
<style lang="scss">

</style>