<template>
    <section>
        <div class="card" v-for="(film, index) in films" :key="index">
            <img v-if="film.poster_path == null & film.backdrop_path == null" src="https://gazzettadiparma-stage.dsharecloud.com/static/img/foglia/locandina-non-disponibile.jpg" :alt="film.title">
            <img v-else-if="film.backdrop_path != null" :src="preLink + film.backdrop_path" :alt="film.title">
            <img v-else :src="preLink + film.poster_path" :alt="film.title">
        <div class="layover">
            <h4>Titolo: {{film.name}}</h4>
            <h4>Titolo originale: {{film.original_title}}</h4>
            <img id="flag" src="../assets/images/en.png" v-if="film.original_language == 'en'">
            <h4 v-else>Lingua: {{film.original_language}}</h4>
            <img id="flag" src="../assets/images/it.png" v-if="film.original_language == 'it'">
            <h4 v-else>Lingua: {{film.original_language}}</h4>
            <h4> Voto: <i id="star" :class="number <= voteRound ?'fas fa-star' : 'far fa-star'" v-for="number in 5" :key="number"></i></h4>
            <h4>Overview: {{film.overview}}...</h4>
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
        voteRound: "",
    }
},
methods: {
    
},
updated() {
    this.films.forEach(element => {
        if (element.overview.length > 50) {
            element.overview = element.overview.slice(0,100);
        }
    });
},
computed: {
    vote () {

        this.films.forEach(element => {
        this.voteRound = Math.round(element.vote_average/2);
        });
        console.log(this.voteRound);
        return this.voteRound;
    }

}
}
</script>

<style lang="scss" scoped>
    section {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        .card {
            display: flex;
            justify-content: center;
            position: relative;
            width: 280px;
            height: 150px;
            margin: 1%;
            img {
                width: 100%;
                height: 100%;
                object-fit: initial;
                object-position: center;
            }
        }
    }   
        .layover {
            display: none;
        }
        .card:hover .layover {
            display: inline;
            position: absolute;
            z-index: 1;
            width: 100%;
            height: 100%;
            padding: 10px;
            background-color: rgba($color: #525050, $alpha: 0.7);
            #star {
                width: 30px;
                color: rgb(247, 200, 154);
            }
            #flag {
                width: 30px;
                height: 10px;
            }
        }
</style>