<template>
    <div class="col-2 mb-2">
        <div class="card text-center">
            <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w154/${tvCard.poster_path}`" :alt="tvCard.original_name">
            <div class="card-body">
                <h5 class="card-title">{{tvCard.name}}</h5>
                <h6 class="card-title">{{tvCard.original_name}}</h6>
                <p class="m-0">
                    <lang-flag :iso="tvCard.original_language"/>
                </p>
                <p class="m-0">{{starsVote(tvCard.vote_average)}} {{int}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TvCard',
    props: {'tvCard' : Object},
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