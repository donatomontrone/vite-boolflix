<template>
    <HeaderComponent @searchMovie="getMovies" />
    <MainComponent />
</template>
<script>
import { store } from '../store.js';
import axios from 'axios';
import HeaderComponent from './HeaderComponent.vue';
import MainComponent from './MainComponent.vue';
export default {
    // Components figli diretti dell'APiCallComponent.vue
    components: {
        HeaderComponent,
        MainComponent
    },
    data() {
        return {
            store,
            apiUrl: 'https://api.themoviedb.org/3/search/movie',
            personalKey: 'a24620df747ffd09f092e18dcb8eab65',
        }
    },
    methods: {
        getMovies(queryInput) {
            axios.get(this.apiUrl, {
                params: {
                    api_key: this.personalKey,
                    query: queryInput,
                }
            })
                .then((response) => {
                    // this.store.arraydovesalvare = (response.data.'cercare il dato che mi interessa');
                    this.store.cards = (response.data.results);
                    console.log(response.data.results)

                })
                .catch(function (error) {
                    // handle error
                    console.error(error);
                })
        }
    },
    created() {
        this.getMovies();
    }
}
</script>
<style scoped>

</style>