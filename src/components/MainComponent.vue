<template>
    <main>
        <h2>Main</h2>
        <!-- Inserire il components che continete la cardList presa dalla chiamata Ajax -->
        <CardListComponent />
    </main>
</template>
<script>
import CardListComponent from './CardListComponent.vue';
export default {
    name: 'MainComponent',
    components: {
        CardListComponent,
    }
}
</script>
<style lang="scss" scoped>

</style>