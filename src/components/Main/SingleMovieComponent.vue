<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-4 d-flex">
        <div class="card w-100 h-100">
            <div class="card-body">
                <h5 class="card-title">{{ movieInfo.title }}</h5>
                <h5 class="card-title" :class="(movieInfo.title === movieInfo.original_title ? 'd-none' : '')">{{
                    movieInfo.original_title
                }}</h5>
                <h5> {{ movieInfo.original_language }}</h5>
                <img v-if="languages.includes(movieInfo.original_language)"
                    :src="getImagePath(movieInfo.original_language)">
                <img v-else :src="getImagePath('xx')">
                <h5 class="card-title">{{ movieInfo.vote_average }}</h5>
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
        getImagePath: function (img) {
            return new URL((`../../assets/flag-icon/${img}.svg`), import.meta.url).href;
        }
    },
}
</script>
<style lang="scss" scoped>

</style>