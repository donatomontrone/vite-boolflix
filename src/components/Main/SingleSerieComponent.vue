<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-6 col-sm-4 col-md-3 col-lg-2 d-flex">
        <div class="serie-info d-flex flex-column">
            <img v-if="seriePoster != null" :src="`https://image.tmdb.org/t/p/w342/${seriePoster}`" class="img-fluid"
                :alt="serieName">
            <img v-else :src="getPath('no-cover.jpg')" :alt="serieName">
            <!-- <div class="hover">
            <h5 class="card-title">{{ serieName }}</h5>
            <h5 class="card-title" :class="(serieName === serieOriginalName ? 'd-none' : '')">{{ serieOriginalName }}
            </h5>

                <div class="flag-img">
                    <img v-if="languages.includes(serieLanguage)" :src="getPath('flag-icon/' + serieLanguage + '.svg')"
                        :alt="serieLanguage + 'flag'">
                    <img v-else :src="getPath('flag-icon/xx.svg')" :alt="serieLanguage + 'flag'">
                </div>
                <div class="stars-container">
                    <i v-for="(star, index) in 5" class="fa-star" :class="index < serieVote ? 'fas' : 'far'"></i>
                </div>
            </div> -->
        </div>
    </div>
</template>
<script>
export default {
    name: 'SingleSerieComponent',
    props: {
        serieLanguage: String,
        serieName: String,
        serieOriginalName: String,
        seriePoster: String,
        serieVote: Number,
        serieOverview: String
    },
    data() {
        return {
            languages: ['de', 'en', 'es', 'fr', 'it', 'ja', 'nl', 'pt', 'ru', 'zh']
        }
    },
    methods: {
        getPath: function (img) {
            return new URL((`../../assets/${img}`), import.meta.url).href;
        }
    },
}
</script>
<style lang="scss" scoped>

</style>