<template>
    <!-- Eseguire in v for sulla singola card -->
    <div class="container-sm">
        <div class="row">
            <div class="col-12">
                <h2 v-if="store.series.length > 0">Serie TV</h2>
            </div>
        </div>
        <div class="row gx-1 gy-5">
            <SingleSerieComponent v-for="serie in store.series" :serieLanguage="serie.original_language"
                :serieName="serie.name" :serieOriginalName="serie.original_name" :seriePoster="serie.poster_path"
                :serieVote="Math.ceil(serie.vote_average / 2)" :serieOverview="serie.overview" />
        </div>
    </div>
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