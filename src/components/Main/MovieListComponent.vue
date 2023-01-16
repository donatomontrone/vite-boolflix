<template>
    <!-- Eseguire in v for sulla singola card -->
    <div class="container-sm mb-5">
        <div class="row">
            <div class="col-12">
                <h2 v-if="store.movies.length > 0">Film</h2>
            </div>
        </div>
        <div class="row gx-1 gy-5">
            <SingleMovieComponent v-for="movie in store.movies" :movieLanguage="movie.original_language"
                :movieTitle="movie.title" :movieOriginalTitle="movie.original_title" :moviePoster="movie.poster_path"
                :movieVote="Math.ceil(movie.vote_average / 2)" :movieOverview="movie.overview" />
        </div>
    </div>
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