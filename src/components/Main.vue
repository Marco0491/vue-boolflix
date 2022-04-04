<template>
    <main>
        <div class="container-fluid">
            <div class="row p-5">
                <MovieCard v-for="element in moviesList" :key="element.id" :movieCard='element'/>
                <TvCard v-for="element in tvShowList" :key="element.id" :tvCard='element'/>
            </div>
        </div>
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue';
import TvCard from './TvCard.vue';

export default {
    name: 'IndexMain',
    props: {
        'moviesList' : Array,
        'tvShowList' : Array,
        },
    components: {
        MovieCard,
        TvCard,
    },
};
</script>

<style lang='scss' scoped>
    main {
        height: 90vh;
        background-color: lightgray;
        overflow-y: scroll;
    }
</style>