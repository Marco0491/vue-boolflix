<template>
    <div class="col-3 mb-2">
        <div class="card">
            <img class="img-fluid" :src="`https://image.tmdb.org/t/p/w342/${movieCard.poster_path}`" :alt="movieCard.original_title">
            <div class="card-body">
                <div class="title mb-1">
                    <span class="text-capitalize fw-bold">titolo: </span>
                    <span>{{movieCard.title}}</span>
                </div>
                <div class="original-title mb-1">
                    <span class="text-capitalize fw-bold">titolo originale: </span>
                    <span>{{movieCard.original_title}}</span>
                </div>
                <div class="lang mb-1">
                    <p class="m-0">
                        <span class="text-capitalize fw-bold">lingua: </span>
                        <lang-flag :iso="movieCard.original_language"/>
                    </p>
                </div>
                <div class="vote mb-1">
                    <p class="m-0">
                        <span class="text-capitalize fw-bold">voto: </span>
                        <span v-for="stars in starsVote(movieCard.vote_average)" :key="`star-${stars}`">
                            <font-awesome-icon icon="fa-solid fa-star" />
                        </span>
                        <span v-for="stars in 5 - starsVote(movieCard.vote_average)" :key="`star-2-${stars}`">
                            <font-awesome-icon icon="fa-regular fa-star" />
                        </span>
                    </p>
                </div>
                <div class="overview">
                    <span class="text-capitalize fw-bold">overview: </span>
                    <span>{{movieCard.overview}}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {'movieCard' : Object},
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
div.card {
    height: 350px;
    font-size: 0.8rem;
    position: relative;
    overflow-y: auto;
    img {
        height: 100%;
    }
    div.card-body {
        width: 100%;
        display: none;
        color: white;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    &:hover div.card-body {
        display: block;
    }
    &:hover img {
        filter: brightness(0.2);
    }
}
</style>