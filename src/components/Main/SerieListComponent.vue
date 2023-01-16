<template>
    <!-- Eseguire in v for sulla singola card -->
    <div class="container">
        <div class="row">
            <h2 v-if="store.series.length > 0">Serie TV</h2>
            <SingleSerieComponent v-for="serie in store.series" :serieInfo="serie" />
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