<!-- Importo esclusivamente il component per effettuare la chìamata ajax -->
<script>
import ApiCallComponent from './components/ApiCallComponent.vue';
export default {
  // Components figli diretti dell'App.vue
  components: {
    ApiCallComponent,
  },
}
</script>
<template>
  <ApiCallComponent />
</template>

<!-- Nello Style importo i miei fogli custom di scss e Bootstrap -->
<style lang="scss">
@use './styles/partials/variables.scss' as *;
@use './styles/general.scss' as *;
@use 'bootstrap/scss/bootstrap.scss' as *;
</style>
