<template>
    <!-- Inserire il components che continete la cardList presa dalla chiamata Ajax -->
    <main>
        <div class="container-sm">
            <div class="row gx-1 gy-5">
                <ListComponent />
            </div>
        </div>
    </main>
</template>
<script>
import ListComponent from './ListComponent.vue';
export default {
    name: 'MainComponent',
    components: {
        ListComponent
    }
}
</script>
<style lang="scss" scoped>

</style>