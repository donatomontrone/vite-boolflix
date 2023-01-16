<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-4 d-flex">
        <div class="card w-100 h-100">
            <div class="card-body">
                <img v-if="movieInfo.poster_path != null"
                    :src="`https://image.tmdb.org/t/p/w342/${movieInfo.poster_path}`" class="img-fluid"
                    :alt="movieInfo.title">
                <img v-else :src="getPath('no-cover.jpg')" class="img-fluid" :alt="movieInfo.title">
                <h5 class="card-title">{{ movieInfo.title }}</h5>
                <h5 class="card-title" :class="(movieInfo.title === movieInfo.original_title ? 'd-none' : '')">{{
                    movieInfo.original_title
                }}</h5>
                <div class="flag-img">
                    <img v-if="languages.includes(movieInfo.original_language)"
                        :src="getPath('flag-icon/' + movieInfo.original_language + '.svg')"
                        :alt="movieInfo.original_language + 'flag'">
                    <img v-else :src="getPath('flag-icon/xx.svg')" :alt="movieInfo.original_language + 'flag'">
                </div>
                <!-- Faccio diventare il numero del rating da 1 a 5 aprrosimandolo anche per eccesso. -->
                <h5 class="card-title">{{ Math.ceil(movieInfo.vote_average / 2) }}</h5>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'SingleMovieComponent',
    props: [
        'movieInfo'
    ],
    data() {
        return {
            languages: ['de', 'en', 'es', 'fr', 'it', 'ja', 'nl', 'pt', 'ru', 'zh']
        }
    },
    methods: {
        getPath: function (img) {
            return new URL((`../../assets/${img}`), import.meta.url).href;
        },
    },
}
</script>
<style lang="scss" scoped>

</style>