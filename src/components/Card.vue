<template>
    <section>
        <div class="card" v-for="(film, index) in films" :key="index">
            <img :src="preLink + film.backdrop_path" :alt="film.title">
        <div class="layover">
            <h4>Titolo: {{film.name}}</h4>
            <h4>Titolo originale: {{film.original_title}}</h4>
            <img id="flag" src="../assets/images/en.png" v-if="film.original_language == 'en'">
            <h4 v-else>{{film.original_language}}</h4>
            <img id="flag" src="../assets/images/it.png" v-if="film.original_language == 'it'">
            <h4 v-else>{{film.original_language}}</h4>
            <h4>Voto: {{film.vote_average}}</h4>
            <h4>Overview: {{film.overview}}</h4>
        </div>
        </div>
    </section>
</template>

<script>
export default {
name: "Card",
props:["films"],
data () {
    return {
        preLink: "https://image.tmdb.org/t/p/w342",
    }
}
}
</script>

<style lang="scss" scoped>
    section {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        .card {
            display: flex;
            justify-content: center;
            position: relative;
            width: 200px;
            height: 250px;
            margin: 1%;
            img {
                width: 100%;
                height: 100%;
                object-fit: initial;
                object-position: center;
            }
            #flag {
                width: 30px;
                height: 10px;
            }
        }
        .layover {
            position: absolute;
            z-index: 1;
            width: 100%;
            height: 100%;
            padding: 10px;
            background-color: rgba($color: #525050, $alpha: 0.7);
        }
    }
</style>