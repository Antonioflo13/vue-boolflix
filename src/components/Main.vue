<template>
    <main>
        <section>
            <h2>I più popolari su Boolflix</h2>
            <article>
            <Card v-for="(popular, index) in populars" :key="index" :item="popular"/>
            </article>
        </section>
        <section>
            <h2>I titoli del momento</h2>
            <article>
            <Card v-for="(topRated, index) in topRateds" :key="index" :item="topRated"/>
            </article>
        </section>
        <section>
            <h2>Drammi TV stile soap</h2>
            <article>
            <Card v-for="(popular, index) in populars" :key="index" :item="popular"/>
            </article>
        </section>
        <section>
            <h2>Film Italiani</h2>
            <article>
            <Card v-for="(popular, index) in populars" :key="index" :item="popular"/>
            </article>
        </section>
        <section>
            <article>
            <Card v-for="(films, index) in films" :key="index" :item="films"/>
            </article>
        </section>
    </main>
</template>

<script>
import Card from '../components/Card.vue'

export default {
    name: "Main",
    components: {
        Card,
    },
    props:["films", "populars", "topRateds"],
    data() {
        return {
            transform: ""
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '../style/mixin.scss';
    main {  
        height: 100%;
            background-color: #151515;
        section {
            @include wrapper;
            display: flex;
            flex-direction: column;
            padding: 0px 0 15px 0;
            h2 {
                padding: 10px 0;
            }
            article {
                display: flex;
                flex-wrap: wrap;
            }
        }
    }
</style>