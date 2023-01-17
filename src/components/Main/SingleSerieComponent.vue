<template>
    <div class="col-6 col-sm-4 col-md-3 col-lg-2 d-flex card-container">
        <div class="serie-info d-flex flex-column  w-100 h-100">
            <img :src="seriePoster != null ? `https://image.tmdb.org/t/p/w342/${seriePoster}` : getPath('no-cover.jpg')"
                class="img-fluid" :alt="serieName">
            <div class="hover overflow-auto">
                <p class="card-title">{{ serieName }}</p>
                <p class="card-title" :class="(serieName === serieOriginalName ? 'd-none' : '')">{{ serieOriginalName }}
                </p>
                <div class="stars-container">
                    <p>Vote: <i v-for="(star, index) in 5" class="fa-star"
                            :class="index < serieVote ? 'fas' : 'far'"></i>
                    </p>
                </div>
                <p>{{ serieOverview }}</p>
                <div class="flag-img">
                    <span class="d-inline-block">Language: </span>
                    <img :src="languages.includes(serieLanguage) ? getPath('flag-icon/' + serieLanguage + '.svg') : getPath('flag-icon/xx.svg')"
                        :alt="serieLanguage + 'flag'" class="d-inline-block">
                </div>
            </div>
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
            languages: ['de', 'en', 'es', 'fr', 'it', 'ja', 'nl', 'pt', 'ru', 'zh'],
            activeHover: false,
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