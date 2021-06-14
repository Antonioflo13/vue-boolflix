<template>
    <section>
        <div class="card" v-for="(film, index) in films" :key="index">
            <img src="film.backdrop_path" alt="film.backdrop_path">
            <h4>{{film.title}}</h4>
            <h4>{{film.original_title}}</h4>
            <img id="flag" src="../assets/images/en.png" v-if="film.original_language == 'en'">
            <img id="flag" src="../assets/images/it.png" v-if="film.original_language == 'it'">
            <h4>{{film.vote_average}}</h4>
        </div>
    </section>
</template>

<script>
export default {
name: "Card",
props:["films"]
}
</script>

<style lang="scss" scoped>
    section {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        .card {
            width: 300px;
            height: 300px;
            margin: 1%;
            background-color: blue;
            #flag {
                width: 50px;
            }
        }
    }
</style>