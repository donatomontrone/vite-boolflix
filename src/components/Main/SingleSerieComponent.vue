<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-4 d-flex">
        <div class="card w-100 h-100">
            <div class="card-body">
                <img v-if="serieInfo.poster_path != null"
                    :src="`https://image.tmdb.org/t/p/w342/${serieInfo.poster_path}`" class="img-fluid"
                    :alt="serieInfo.title">
                <img v-else :src="getPath('no-cover.jpg')" :alt="serieInfo.title">
                <h5 class="card-title">{{ serieInfo.original_name }}</h5>
                <h5 class="card-title" :class="(serieInfo.name === serieInfo.original_name ? 'd-none' : '')">{{
                    serieInfo.original_name
                }}</h5>
                <div class="flag-img">
                    <img v-if="languages.includes(serieInfo.original_language)"
                        :src="getPath('flag-icon/' + serieInfo.original_language + '.svg')"
                        :alt="serieInfo.original_language + 'flag'">
                    <img v-else :src="getPath('flag-icon/xx.svg')" :alt="serieInfo.original_language + 'flag'">
                </div>
                <!-- Faccio diventare il numero del rating da 1 a 5 aprrosimandolo anche per eccesso. -->
                <h5 class="card-title">{{ Math.ceil(serieInfo.vote_average / 2) }}</h5>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'SingleMovieComponent',
    props: [
        'serieInfo'
    ],
    data() {
        return {
            languages: ['de', 'en', 'es', 'fr', 'it', 'ja', 'nl', 'pt', 'ru', 'zh']
        }
    },
    methods: {
        getFlagUrlPath: function (img) {
            return new URL((`../../assets/${img}`), import.meta.url).href;
        }
    },
}
</script>
<style lang="scss" scoped>

</style>