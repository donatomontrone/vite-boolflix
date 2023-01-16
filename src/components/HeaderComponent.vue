<template>
    <header>
        <!-- Inseirire l'header con la search bar  -->
        <nav class="navbar bg-black">
            <div class="container-fluid">
                <a class="navbar-brand text-white">Navbar</a>
                <div class="d-flex" role="search">
                    <input class="form-control me-2" placeholder="Search" v-model="userInput"
                        @keyup.enter="$emit('searchMovie', userInput)">
                    <a class="btn btn-outline-success" @click="$emit('searchMovie', userInput)">Search</a>
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

</style>