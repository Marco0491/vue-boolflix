<template>
    <div class="col-2 mb-2">
        <div class="card text-center">
            <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w154/${movieCard.poster_path}`" :alt="movieCard.original_title">
            <div class="card-body">
                <h5 class="card-title">{{movieCard.title}}</h5>
                <h6 class="card-title">{{movieCard.original_title}}</h6>
                <p class="m-0">
                    <lang-flag :iso="movieCard.original_language"/>
                </p>
                <p class="m-0">{{starsVote(movieCard.vote_average)}} {{int}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {'movieCard' : Object},
    data: function() {
        return {
            int: '',
        }
    },
    methods: {
        starsVote(number) {
            this.int = parseInt(Math.round(number / 2));
        }
    },
};
</script>

<style lang='scss' scoped>
</style>