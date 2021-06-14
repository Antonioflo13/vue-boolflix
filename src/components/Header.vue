<template>
    <header>
        <nav>
            <div class="nav-right">
                <ul>
                    <li><a href="">logo</a></li>
                </ul>
            </div>
            <div class="nav-left">
                <ul>
                <li><a href="">Home</a></li>
                <li><a href="">Serie TV</a></li>
                <li><a href="">Film</a></li>
                <li><a href="">Nuovi Arrivi</a></li>
                <li><a href="">La mia lista</a></li>
                <li><input type="search" name="" id="" v-model="search" @keydown="$emit('search', search)"></li>
                <li><a href="">notifiche</a></li>
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
        }
    },
    methods: {
    }
}
</script>

<style lang="scss" scoped>
    @import '../style/mixin.scss';
    header {
        background-color: black;
        nav {
            display: flex;
            justify-content: space-between;
            width: 100%;
            position: fixed;
            padding: 15px 10px;
            ul li {
                display: inline;
                list-style: none;
                a {
                    padding: 10px 15px;
                    text-decoration: none;
                    color: white;
                }
            }
        }
    }
</style>