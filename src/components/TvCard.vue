<template>
    <div class="col-3 mb-2">
        <div class="card">
            <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w342/${tvCard.poster_path}`" :alt="tvCard.original_name">
            <div class="card-body">
                <div class="title mb-1">
                    <span class="text-capitalize fw-bold">titolo: </span>
                    <span>{{tvCard.name}}</span>
                </div>
                <div class="original-title mb-1">
                    <span class="text-capitalize fw-bold">titolo originale: </span>
                    <span>{{tvCard.original_name}}</span>
                </div>
                <div class="lang mb-1">
                    <p class="m-0">
                        <span class="text-capitalize fw-bold">lingua: </span>
                        <lang-flag :iso="tvCard.original_language"/>
                    </p>
                </div>
                <div class="vote mb-1">
                    <p class="m-0">
                        <span class="text-capitalize fw-bold">voto: </span>
                        <span v-for="stars in starsVote(tvCard.vote_average)" :key="`star-${stars}`">
                            <font-awesome-icon icon="fa-solid fa-star" />
                        </span>
                        <span v-for="stars in 5 - starsVote(tvCard.vote_average)" :key="`star-2-${stars}`">
                            <font-awesome-icon icon="fa-regular fa-star" />
                        </span>
                    </p>
                </div>
                <div class="overview">
                    <span class="text-capitalize fw-bold">overview: </span>
                    <span>{{tvCard.overview}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TvCard',
    props: {'tvCard' : Object},
    data: function() {
        return {}
    },
    methods: {
        starsVote(number) {
            return parseInt(Math.round(number / 2));
        }
    },
};
</script>

<style lang='scss'>
</style>