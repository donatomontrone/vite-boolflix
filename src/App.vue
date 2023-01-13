<script>
import { store } from './store.js';
import axios from 'axios';
export default {
  components: {

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
  <h1>App.vue</h1>
</template>

<style lang="scss">
@use './styles/partials/variables.scss' as *;
@use './styles/general.scss' as *;
@use 'bootstrap/scss/bootstrap.scss' as *;
</style>
