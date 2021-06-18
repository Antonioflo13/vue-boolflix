<template>
    <header>
        <nav :class="{ 'onScroll': !topOfPage}">
            <div class="nav-right">
                <ul>
                    <li><a href=""><img src="https://fontmeme.com/permalink/210614/0a43aa36584f2895324a0006b42b5d1a.png" alt="logo"></a></li>
                    <li><a href="">Home</a></li>
                    <li><a href="">Serie TV</a></li>
                    <li><a href="">Film</a></li>
                    <li><a href="">Nuovi Arrivi</a></li>
                    <li><a href="">La mia lista</a></li>
                </ul>
            </div>
            <div class="nav-left">
                <ul>
                    <li>
                        <input type="search" name="" id="" placeholder="Titoli" v-model="search" v-if="clicked" @change="searchValue">
                    </li>
                    <li><i id="search" class="fas fa-search" @click="clicked=!clicked"></i></li>
                    <li><i id="notice" class="far fa-bell"></i></li>
                </ul>
            </div>
        </nav>
        <div class="jumbotron">
            <video src="../assets/Stranger Things 4 _ Undici, stai ascoltando.mp4" width="100%" height="550px" autoplay muted loop=1></video>
            <audio id="audio" src="../assets/videoplayback.mp4" loop=1></audio>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data () {
        return {
            search: "",
            clicked: false,
            topOfPage: true,
        }
    },
    methods: {
        searchValue() {
            this.$emit('search', this.search);
        },
        clickSearch() {
            this.clicked = true;
        },
        audio() {
            document.getElementById('audio').play();
        },
        scrolling(){
            if(window.pageYOffset>0){
            if(this.topOfPage) this.topOfPage = false;
            } else {
            if(!this.topOfPage) this.topOfPage = true;
        }
    }
    },
    beforeMount() {
        window.addEventListener('scroll', this.scrolling);
        window.addEventListener('scroll', this.audio);
    }
}
</script>

<style lang="scss" scoped>
    @import '~@fortawesome/fontawesome-free/css/all.min.css';
    @import '../style/mixin.scss';
    .onScroll {
    background-color: rgba($color: #151515, $alpha: 1.0);
    }
    header {
        background-color: #151515;
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            position: fixed;
            z-index: 2;
            padding: 20px 25px;
            transition: ease-out 1s;
            .nav-right {
                img {
                    width: 150px;
                }
            }
            #notice,
            #search {
                font-size: 20px;
                padding: 0 15px;
                color: white;
            }
            ul {
                display: flex;
                align-items: center;
                li {
                    display: inline;
                    list-style: none;
                    a {
                    padding: 10px 10px;
                    text-decoration: none;
                    color: white;
                    }
                    a:hover {
                        color: rgb(148, 147, 147);
                    }
                    i {
                        cursor: pointer;
                    }
                    input {
                        padding: 5px;
                        border: 1px solid white;
                        background-color: black;
                        font-size: 12px;
                        letter-spacing: 1px;
                        color: white;
                        transition: 3s;
                    }
                }
            }
        }
        .jumbotron {
            video {
                object-fit: cover;
            }
        }
    }

    @media screen and (min-width: 320px )  and (max-width: 1024px ) {
        .onScroll {
            background-color: rgba($color: #151515, $alpha: 0.5);
        }
        header {
            nav {
                padding: 10px 0;
                .nav-right {
                    img {
                        width: 100px;
                    }
                    ul li:nth-child(2),
                    ul li:nth-child(3),
                    ul li:nth-child(4),
                    ul li:nth-child(5),
                    ul li:nth-child(6)
                     {
                        display: none;
                    }
                }
            }
        }
        .jumbotron video {
            display: none;
        }
    }
    
</style>