<template>
    <HeaderComponent @searchMovie="getCall" />
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
            apiUrl: 'https://api.themoviedb.org/3/search/',
            personalKey: 'a24620df747ffd09f092e18dcb8eab65',
            apiTrending: 'https://api.themoviedb.org/3/trending/all/week'
        }
    },
    methods: {
        getPopular() {
            axios.get(this.apiTrending, {
                params: {
                    api_key: this.personalKey
                }
            })
                .then((response) => {
                    // this.store.arraydovesalvare = (response.data.'cercare il dato che mi interessa');
                    this.store.popular = (response.data.results);
                    console.log(this.store.popular)

                })
                .catch(function (error) {
                    console.error('Trending' + error);
                });
        },
        callMoviesAndSeries(type, queryInput) {
            //Chiamata per i film
            if (queryInput != '') {
                axios.get(this.apiUrl + type, {
                    params: {
                        api_key: this.personalKey,
                        query: queryInput,
                    }
                })
                    .then((response) => {
                        if (type === 'movie') {
                            this.store.movies = (response.data.results);
                            console.log(this.store.movies)
                        } else {
                            this.store.series = (response.data.results);
                            console.log(response.data.results)
                        }
                    })
                    .catch(function (error) {
                        console.error(error);
                    });
                queryInput = '';
            }
        },
        getCall(queryInput) {
            this.callMoviesAndSeries('movie', queryInput);
            this.callMoviesAndSeries('tv', queryInput);
        }
    },
    created() {
        this.getPopular()
    }

}
</script>
<style scoped>

</style>