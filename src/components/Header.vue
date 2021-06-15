<template>
    <header>
        <nav>
            <div class="nav-right">
                <ul>
                    <li><a href=""><img src="https://fontmeme.com/permalink/210614/0a43aa36584f2895324a0006b42b5d1a.png" alt="logo"></a></li>
                </ul>
            </div>
            <div class="nav-left">
                <ul>
                <li><a href="">Home</a></li>
                <li><a href="">Serie TV</a></li>
                <li><a href="">Film</a></li>
                <li><a href="">Nuovi Arrivi</a></li>
                <li><a href="">La mia lista</a></li>
                <li><input type="search" name="" id="" v-if="clicked == true" v-model="search" @change="searchValue"></li>
                <li><i id="search" class="fas fa-search" @click="clickSearch"></i></li>
                <li><i id="notice" class="far fa-bell"></i></li>
                </ul>
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    name: "Header",
    data () {
        return {
            search: "",
            clicked: false,
        }
    },
    methods: {
        searchValue() {
            this.$emit('search', this.search);
        },
        clickSearch() {
            this.clicked = true;
            
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '~@fortawesome/fontawesome-free/css/all.min.css';
    @import '../style/mixin.scss';
    header {
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            position: fixed;
            z-index: 2;
            @include wrapper;
            background-color: black;
            img {
                width: 60%;
            }
            #notice,
            #search {
                width: 20px;
                padding: 0 15px;
                color: white;
            }
            ul li {
                display: inline;
                list-style: none;
                a {
                    padding: 10px 10px;
                    text-decoration: none;
                    color: white;
                }
            }
        }
    }
</style>