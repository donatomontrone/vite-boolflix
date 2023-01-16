<template>
    <!-- Inserire il template per ogni singola card, dati presi dallo store -->
    <div class="col-4 d-flex">
        <div class="card w-100 h-100">
            <div class="card-body">
                <h5 class="card-title">{{ cardInfo.title }}</h5>
                <h5 class="card-title" :class="(cardInfo.title === cardInfo.original_title ? 'd-none' : '')">{{
                    cardInfo.original_title
                }}</h5>
                <h5 class="card-title">{{ cardInfo.original_language }}</h5>
                <h5 class="card-title">{{ cardInfo.vote_average }}</h5>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'SingleCardComponent',
    props: [
        'cardInfo'
    ],
    data() {
        return {
        }
    },
}
</script>
<style lang="scss" scoped>

</style>