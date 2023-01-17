<template>
    <CardComponent v-for="card in MoviesAndSeriesTv" :cardInfo="card" />
</template>
<script>
import { store } from '../../store.js';
import CardComponent from './CardComponent.vue';
export default {
    name: 'ListComponent',
    data() {
        return {
            store,
        }
    },
    components: {
        CardComponent,
    },
    computed: {
        MoviesAndSeriesTv() {
            return [...this.store.movies, ...this.store.series]
        }
    }
}
</script>
<style lang="scss" scoped>

</style>