<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-6 col-sm-4 col-md-3 col-lg-2 d-flex">
        <div class="film-info d-flex flex-column">
            <img v-if="moviePoster != null" :src="`https://image.tmdb.org/t/p/w342/${moviePoster}`" class="img-fluid"
                :alt="movieTitle">
            <img v-else :src="getPath('no-cover.jpg')" class="img-fluid" :alt="movieTitle">
            <!-- <h5 class="card-title">{{ movieTitle }}</h5>
        <h5 class="card-title" :class="(movieTitle === movieOriginalTitle ? 'd-none' : '')">{{ movieOriginalTitle }}
        </h5>
        <div class="flag-img">
            <img v-if="languages.includes(movieLanguage)" :src="getPath('flag-icon/' + movieLanguage + '.svg')"
                :alt="movieLanguage + 'flag'">
            <img v-else :src="getPath('flag-icon/xx.svg')" :alt="movieLanguage + 'flag'">
        </div>
        <h5 class="card-title">{{ movieVote }}</h5>
        <i v-for="(star, index) in 5" class="fa-star" :class="index < movieVote ? 'fas' : 'far'"></i> -->
        </div>
    </div>
</template>
<script>
export default {
    name: 'SingleMovieComponent',
    props: {
        movieLanguage: String,
        movieTitle: String,
        movieOriginalTitle: String,
        moviePoster: String,
        movieVote: Number,
        movieOverview: String
    },
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