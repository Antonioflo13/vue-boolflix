<template>
    <main>
        <section>
            <Card :films=films />
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
    props:["films"]
}
</script>

<style lang="scss" scoped>
    @import '../style/mixin.scss';
    main {
            background-color: black;
        section {
            @include wrapper;
            padding: 50px 0 30px 0;
        }
    }
</style>