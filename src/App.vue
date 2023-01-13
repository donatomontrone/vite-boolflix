<!-- Importo lo store.js e axios per effettuare la chiamata AJAX all'API e salvo i dati in un array che è contenuto nello store. -->
<script>
import { store } from './store.js';
import axios from 'axios';
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
export default {
  // COmponents figli diretti dell'App.vue
  components: {
    HeaderComponent,
    MainComponent
  },
  data() {
    return {
      store,
      apiUrl: "apiurl",
    }
  },
  methods: {
    getAjaxCall() {
      axios.get(this.apiUrl, {
        params: {
        }
      })
        .then((response) => {
          // this.store.arraydovesalvare = (response.data.'cercare il dato che mi interessa');

        })
        .catch(function (error) {
          // handle error
          console.error(error);
        })
    }
  },
  created() {
    this.getAjaxCall();
  }
}
</script>
<template>
  <HeaderComponent />
  <MainComponent />
</template>

<!-- Nello Style importo i miei fogli custom di scss e Bootstrap -->
<style lang="scss">
@use './styles/partials/variables.scss' as *;
@use './styles/general.scss' as *;
@use 'bootstrap/scss/bootstrap.scss' as *;
</style>
