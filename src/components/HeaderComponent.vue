<template>
    <header class="mb-4">
        <!-- Inseirire l'header con la search bar  -->
        <nav class="navbar">
            <div class="container-sm">
                <a class="navbar-brand" @click="$emit('popular')"><img src="/boolflix.png" alt="Boolflix Logo"></a>
                <div class="d-flex" role="search">
                    <input class="form-control me-2" placeholder="Search" v-model="store.userInput">
                    <a class="btn text-white" @click="$emit('searchMovie', store.userInput)"><i
                            class="fa-solid fa-magnifying-glass"></i></a>
                </div>
            </div>
        </nav>
    </header>
</template>
<script>
import { store } from '../store.js'
export default {
    name: 'HeaderComponent',
    data() {
        return {
            store,
        }
    },

}
</script>
<style lang="scss" scoped>
@use '../styles/partials/variables' as *;

header {
    background: rgb(6, 6, 6);
    background: linear-gradient(0deg, rgba(17, 17, 17, 1) 9%, rgba(6, 6, 6, 1) 60%);
}

nav a {
    cursor: pointer;
}

nav img {
    width: 120px;
}
</style>