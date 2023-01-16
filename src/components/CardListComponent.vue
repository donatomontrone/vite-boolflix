<template>
    <!-- Eseguire in v for sulla singola card -->
    <div class="container">
        <div class="row">
            <SingleCardComponent v-for="card in store.cards" :cardInfo="card" />
        </div>
    </div>
</template>
<script>
import { store } from '../store.js';
import SingleCardComponent from './SingleCardComponent.vue';
export default {
    name: 'CardListComponent',
    components: {
        SingleCardComponent,
    },
    data() {
        return {
            store,
        }
    },
}
</script>
<style lang="scss">

</style>