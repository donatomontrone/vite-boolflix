<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-4 d-flex">
        <div class="card w-100 h-100">
            <div class="card-body">
                <h5 class="card-title">{{ serieInfooriginal_name }}</h5>
                <h5 class="card-title" :class="(serieInfo.name === serieInfo.original_name ? 'd-none' : '')">{{
                    serieInfo.original_name
                }}</h5>
                <h5> {{ serieInfo.original_language }}</h5>
                <img v-if="languages.includes(serieInfo.original_language)"
                    :src="getImagePath(serieInfo.original_language)">
                <img v-else :src="getImagePath('xx')">
                <h5 class="card-title">{{ serieInfo.vote_average }}</h5>
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
        getImagePath: function (img) {
            return new URL((`../../assets/flag-icon/${img}.svg`), import.meta.url).href;
        }
    },
}
</script>
<style lang="scss" scoped>

</style>