<template>
    <div class="col-6 col-sm-4 col-md-3 col-lg-2 d-flex card-container">
        <div class="film-info d-flex flex-column w-100 h-100">
            <img :src="moviePoster != null ? `https://image.tmdb.org/t/p/w342/${moviePoster}` : getPath('no-cover.jpg')"
                class="img-fluid" :alt="movieTitle">
            <div class="hover">
                <p class="card-title">{{ movieTitle }}</p>
                <p class="card-title" :class="(movieTitle === movieOriginalTitle ? 'd-none' : '')">{{
                    movieOriginalTitle
                }} </p>
                <div class="stars-container">
                    <p>Vote: <i v-for="(star, index) in 5" class="fa-star"
                            :class="index < movieVote ? 'fas' : 'far'"></i>
                    </p>
                    <p>{{ movieOverview }}</p>
                    <div class="flag-img">
                        <span class="d-inline-block">Language: </span>
                        <img :src="languages.includes(movieLanguage) ? getPath('flag-icon/' + movieLanguage + '.svg') : getPath('flag-icon/xx.svg')"
                            :alt="movieLanguage + 'flag'" class="d-inline-block">
                    </div>
                </div>
            </div>
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
            languages: ['de', 'en', 'es', 'fr', 'it', 'ja', 'nl', 'pt', 'ru', 'zh'],
            activeHover: false,
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