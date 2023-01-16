<template>
    <!-- Eseguire in v for sulla singola card -->
    <div class="container">
        <div class="row">
            <h2 v-if="store.movies.length > 0">Film</h2>
            <SingleMovieComponent v-for="movie in store.movies" :movieInfo="movie" />
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