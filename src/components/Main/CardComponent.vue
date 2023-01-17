<template>
    <div class="col-6 col-sm-4 col-md-3 col-lg-2 d-flex card-container">
        <div class="info d-flex flex-column w-100 h-100">
            <img :src="cardInfo.poster_path != null ? `https://image.tmdb.org/t/p/w342${cardInfo.poster_path}` : getImagePath('no-cover.jpg')"
                class="h-100" :alt="titleOrName()">
            <div class="hover">
                <p class="card-title">{{ titleOrName() }}</p>
                <p class="card-title" :class="(titleOrName() === OriginalTitleOrName() ? 'd-none' : '')">{{
                    OriginalTitleOrName()
                }} </p>
                <div class="stars-container">
                    <p>Vote: <i v-for="(star, index) in 5" class="fa-star"
                            :class="index < getVote() ? 'fas' : 'far'"></i>
                    </p>
                </div>
                <p>{{ cardInfo.overview }}</p>
                <div class="language-flag">
                    <span class="d-inline-block">Language: </span>
                    <img :src="(cardInfo.original_language === 'zh' || 'cn') ? getImagePath('/flag-icon/zh.svg') : `https://crowdin.com/images/flags/${cardInfo.original_language}.png`"
                        :alt="cardInfo.original_language + 'flag'" class="flag-img ms-2 d-inline-block">
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { store } from '../../store.js';
export default {
    name: 'CardComponent',
    props: [
        'cardInfo'
    ],
    data() {
        return {
            languages: ['de', 'en', 'es', 'fr', 'it', 'ja', 'nl', 'pt', 'ru', 'zh'],
            store,

        }
    },
    methods: {
        getVote() {
            return Math.ceil(this.cardInfo.vote_average / 2);
        },
        titleOrName() {
            if (this.cardInfo.title) {
                return this.cardInfo.title
            } else {
                return this.cardInfo.name
            }
        },
        OriginalTitleOrName() {
            if (this.cardInfo.original_title) {
                return this.cardInfo.original_title
            } else {
                return this.cardInfo.original_name
            }
        },
        getImagePath: function (img) {
            return new URL((`../../assets/${img}`), import.meta.url).href;
        },
    }
}
</script>
<style lang="scss" scoped>
@use '../../styles/partials/variables' as *;

div.card-container {
    height: 250px;
}

img.flag-img {
    width: 30px;
}

div.info {
    position: relative;
    transition: 1s ease;
    height: 100%;
}

div.hover {
    font-size: .8rem;
    padding: 1rem .7rem .7rem;
    display: flex;
    flex-direction: column;
    position: absolute;
    overflow: scroll;
    height: 100%;
    width: 100%;
    opacity: 0;
    transition: 1s ease;
    z-index: 1;
    background: rgb(0, 0, 0);
    background: linear-gradient(0deg, rgba(0, 0, 0, .8) 29%, rgba(0, 0, 0, .3) 60%);
}

div.info:hover .hover {
    opacity: 1;
}

div.info:hover {
    transform: scale(1.3);
    z-index: 1;
}

.fa-star {
    color: $star-color;
}
</style>