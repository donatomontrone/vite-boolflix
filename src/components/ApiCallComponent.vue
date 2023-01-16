<template>
    <HeaderComponent @searchMovie="getMoviesAndSeries" />
    <MainComponent />
</template>
<script>
import { store } from '../store.js';
import axios from 'axios';
import HeaderComponent from './HeaderComponent.vue';
import MainComponent from './Main/MainComponent.vue';
export default {
    // Components figli diretti dell'APiCallComponent.vue
    components: {
        HeaderComponent,
        MainComponent
    },
    data() {
        return {
            store,
            apiMoviesUrl: 'https://api.themoviedb.org/3/search/movie',
            apiSeriesUrl: 'https://api.themoviedb.org/3/search/tv',
            personalKey: 'a24620df747ffd09f092e18dcb8eab65',
        }
    },
    methods: {
        getMoviesAndSeries(queryInput) {
            //Chiamata per i film
            axios.get(this.apiMoviesUrl, {
                params: {
                    api_key: this.personalKey,
                    query: queryInput,
                }
            })
                .then((response) => {
                    // this.store.arraydovesalvare = (response.data.'cercare il dato che mi interessa');
                    this.store.movies = (response.data.results);
                    console.log(response.data.results)

                })
                .catch(function (error) {
                    console.error(error);
                });

            //Chiamata per le serie tv
            axios.get(this.apiSeriesUrl, {
                params: {
                    api_key: this.personalKey,
                    query: queryInput,
                }
            })
                .then((response) => {
                    // this.store.arraydovesalvare = (response.data.'cercare il dato che mi interessa');
                    this.store.series = (response.data.results);
                    console.log(response.data.results)

                })
                .catch(function (error) {
                    console.error(error);
                });
        },
    }
}
</script>
<style scoped>

</style>