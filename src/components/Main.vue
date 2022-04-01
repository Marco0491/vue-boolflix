<template>
    <main>
        <div class="container-fluid">
            <div class="row p-5">
                <div v-for="(element, index) in titleList" :key="index" class="col-2">
                    <div class="card text-center">
                        <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w154/${element.poster_path}`" :alt="element.original_title">
                        <div class="card-body">
                            <h5 class="card-title">{{element.title}}</h5>
                            <h6 class="card-title">{{element.original_title}}</h6>
                            <p class="m-0">{{element.original_language}}</p>
                            <p class="m-0">{{element.vote_average}}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import axios from 'axios';

export default {
    name: 'IndexMain',
    props: {'titleToSearch' : String},
    data: function() {
        return {
            titleList: [],
        }
    },
    created() {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=8939b06822f7d93b8f1ab56eeed89c7b&query=batman-begins').then((result) => {this.titleList = result.data.results}).catch((error) => {console.warn(error)})
    }
}
</script>

<style lang='scss' scoped>
    main {
        height: 90vh;
        background-color: lightgray;
    }
</style>