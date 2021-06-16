<template>
    <header>
        <nav>
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
            <video src="../assets/Stranger Things 4 _ Undici, stai ascoltando.mp4" width="100%" height="550px" autoplay muted loop=1 ></video>
            <audio src="../assets/videoplayback.mp4" autoplay @canplay="click"></audio>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    data () {
        return {
            search: "",
            clicked: true,
        }
    },
    methods: {
        searchValue() {
            this.$emit('search', this.search);
        },
        clickSearch() {
            this.clicked = true;
        },
        click(event) {
            console.log(event);
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '~@fortawesome/fontawesome-free/css/all.min.css';
    @import '../style/mixin.scss';
    header {
        background-color: #151515;
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            position: fixed;
            z-index: 2;
            @include wrapper;
            .nav-right {
                padding-left: 50px;
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
        /* Enter and leave animations can use different */
    /* durations and timing functions.              */
    .slide-fade-enter-active {
    transition: all .3s ease;
    }
    .slide-fade-leave-active {
    transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
    }
    .slide-fade-enter, .slide-fade-leave-to
    /* .slide-fade-leave-active below version 2.1.8 */ {
    transform: translateX(10px);
    opacity: 0;
    }
    }
    
</style>