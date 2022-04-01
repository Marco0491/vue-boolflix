<template>
    <div id="app">
        <Header @inputSearch='input'/>
        <Main :titleToSearch='searchedTitle'/>
    </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
    name: 'App',
    components: {
        Header,
        Main
    },
    data: function() {
        return {
            searchedTitle: '',
        }
    },
    methods: {
        input(text) {
            this.searchedTitle = text;
        }
    }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';
</style>
