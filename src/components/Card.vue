<template>
        <div class="card">
            <img v-if="item.poster_path == null & item.backdrop_path == null" src="https://gazzettadiparma-stage.dsharecloud.com/static/img/foglia/locandina-non-disponibile.jpg" :alt="item.title">
            <img v-else-if="item.backdrop_path != null" :src="preLink + item.backdrop_path" :alt="item.title">
            <img v-else :src="preLink + item.poster_path" :alt="item.title">
            <div class="layover">
                <h4 v-if="item.name">Titolo <br> {{item.name}}</h4>
                <h4 v-if="item.original_title">Titolo originale: {{item.original_title}}</h4>
                <img id="flag" src="../assets/images/en.png" v-if="item.original_language == 'en'">
                <img id="flag" src="../assets/images/it.png" v-else-if="item.original_language == 'it'">
                <h4 v-else>Lingua: {{item.original_language}}</h4>
                <h4><i id="star" :class="number <= vote ?'fas fa-star' : 'far fa-star'" v-for="number in 5" :key="number"></i></h4>
                <h4>Overview <br> {{item.overview.slice(0,110) }}...</h4>
            </div>
        </div>
</template>

<script>
export default {
name: "Card",
props:["item"],
data () {
    return {
        preLink: "https://image.tmdb.org/t/p/w342",
        voteRound: "",
    }
},
methods: {
    
},
computed: {
    vote () {
        return Math.round(this.item.vote_average/2);
    }
}
}
</script>

<style lang="scss" scoped>
    @import '../style/mixin.scss';
        .card {
            display: flex;
            justify-content: center;
            position: relative;
            width: calc(100% / 6 - 10px);
            height: 120px;
            margin: 5px;
            img {
                width: 100%;
                height: 100%;
                object-fit: initial;
                object-position: center;
                border-radius: 3%;
            }
        } 
        .layover {
            display: none;
            font-size: 7px;
            h4 {
                padding: 2px;
            }
        }
        .card:hover .layover {
            display: inline;
            position: absolute;
            z-index: 1;
            width: 100%;
            height: 100%;
            padding: 10px;
            margin-left: 30px;
            border-radius: 3%;
            overflow: hidden;
            animation-name: example;
            animation-duration: 1s;
            animation-fill-mode: forwards;
            background-color: #151515;
            cursor: pointer;
        }
            @keyframes example {
            from {transform: scale(1,1);}
            to {transform: scale(1.5,3);}
            }
            #star {
                font-size: 10px;
                color: rgb(247, 200, 154);
            }
            #flag {
                width: 30px;
                height: 10px;
            }
</style>