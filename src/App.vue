<template>
    <div id="app">
        <Header @inputSearch='input'/>
        <Main :moviesList='titleMovieList' :tvShowList='titleTvShowList'/>
    </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
    name: 'App',
    components: {
        Header,
        Main,
    },
    data: function() {
        return {
            searchedTitle: '',
            titleMovieList: [],
            titleTvShowList: [],
        };
    },
    methods: {
        input(text) {
            this.searchedTitle = text;
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=8939b06822f7d93b8f1ab56eeed89c7b&query=${this.searchedTitle}`).then((result) => {this.titleMovieList = result.data.results;}).catch((error) => {console.warn(error)});
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=8939b06822f7d93b8f1ab56eeed89c7b&query=${this.searchedTitle}`).then((result) => {this.titleTvShowList = result.data.results;}).catch((error) => {console.warn(error)});
        },
    },
};
</script>

<style lang="scss">
@import './assets/styles/style.scss';
</style>
