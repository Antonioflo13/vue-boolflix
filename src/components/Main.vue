<template>
    <main>
        <!-- home -->
        <div v-if="!films.length > 0">
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
                    <Card v-for="(soap, index) in soap" :key="index" :item="soap"/>
                </article>
            </section>
            <section>
                <h2>Film Action</h2>
                <article>
                    <Card v-for="(action, index) in action" :key="index" :item="action"/>
                </article>
            </section>
        </div>
        <!-- /home -->

        <!-- search -->
        <section v-else class="search">
            <h2>Films</h2>
            <article>
                <Card v-for="(films, index) in films" :key="index" :item="films"/>
            </article>
            <h2>Serie TV</h2>
            <article>
                <Card v-for="(series, index) in series" :key="index" :item="series"/>
            </article>
        </section>
        <!-- /search -->

    </main>
</template>

<script>
import Card from '../components/Card.vue'

export default {
    name: "Main",
    components: {
        Card,
    },
    props:["films", "populars", "topRateds", "soap", "action", "series"],
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
        .search {
            padding: 30px 0;
        }
    }
</style>