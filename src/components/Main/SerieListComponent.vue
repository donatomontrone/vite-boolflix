<template>
    <!-- Eseguire in v for sulla singola card -->
    <SingleSerieComponent v-for="serie in store.series" :serieLanguage="serie.original_language" :serieName="serie.name"
        :serieOriginalName="serie.original_name" :seriePoster="serie.poster_path"
        :serieVote="Math.ceil(serie.vote_average / 2)" :serieOverview="serie.overview" />
</template>
<script>
import { store } from '../../store.js';
import SingleSerieComponent from './SingleSerieComponent.vue';
export default {
    name: 'SerieListComponent',
    components: {
        SingleSerieComponent,
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