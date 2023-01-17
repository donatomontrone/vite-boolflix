<template>
    <header class="mb-4">
        <!-- Inseirire l'header con la search bar  -->
        <nav class="navbar">
            <div class="container-sm">
                <a class="navbar-brand text-white"><img src="/boolflix.png" alt="Boolflix Logo"></a>
                <div class="d-flex" role="search">
                    <input class="form-control me-2" placeholder="Search" v-model="userInput"
                        @keyup="$emit('searchMovie', userInput)">
                    <a class="btn text-white" @click="$emit('searchMovie', userInput)"><i
                            class="fa-solid fa-magnifying-glass"></i></a>
                </div>
            </div>
        </nav>
    </header>
</template>
<script>

export default {
    name: 'HeaderComponent',
    data() {
        return {
            userInput: ''
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

nav img {
    width: 120px;
}
</style>