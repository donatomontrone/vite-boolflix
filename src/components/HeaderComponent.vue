<template>
    <header>
        <!-- Inseirire l'header con la search bar  -->
        <nav class="navbar bg-black">
            <div class="container-fluid">
                <a class="navbar-brand text-white"><img src="../../public/boolflix.png" alt="Boolflix Logo"></a>
                <div class="d-flex" role="search">
                    <input class="form-control me-2" placeholder="Search" v-model="userInput"
                        @keyup.enter="$emit('searchMovie', userInput)">
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

nav img {
    width: 120px;
}
</style>