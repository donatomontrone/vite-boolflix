<template>
    <!-- Inserire il components che continete la cardList presa dalla chiamata Ajax -->
    <main>
        <SerieListComponent />
        <MovieListComponent />
    </main>
</template>
<script>
import MovieListComponent from './SerieListComponent.vue';
import SerieListComponent from './MovieListComponent.vue';
export default {
    name: 'MainComponent',
    components: {
        MovieListComponent,
        SerieListComponent,
    }
}
</script>
<style lang="scss" scoped>

</style>