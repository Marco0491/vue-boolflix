<template>
	<header class="container-fluid px-5">
        <div class="row px-5">
            <div class="col-12 d-flex justify-content-between">
                <h2 class="text-danger m-0">Boolflix</h2>
                <div class="search d-flex align-items-center">
                    <input v-model="titleInsert" @keyup.enter="$emit('inputSearch', titleInsert)" class="me-2" type="search" placeholder="Search Movie">
                    <button @click="$emit('inputSearch', titleInsert)" class="btn btn-outline-success" type="submit">Search</button>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: 'IndexHeader',
    data: function() {
        return {
            titleInsert: '',
        };
    },
};
</script>

<style lang='scss' scoped>
    header {
        height: 10vh;
        background-color: black;
        h2 {
            line-height: 10vh;
            vertical-align: middle;
        }
        div.search {
            height: 100%;
        }
    }
</style>