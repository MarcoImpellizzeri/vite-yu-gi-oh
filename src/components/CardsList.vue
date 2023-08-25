<script>
import axios from 'axios';
import Card from './Card.vue'
import { store } from '../store'


export default {
    components: {
        Card,
    },
    data() {
        return {
            cards: [],
            store,
        }
    },
    methods: {
        fetchCards(newUrl) {
            const url = newUrl ?? "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0";
            this.loading = true;

            axios.get(url).then((response) => {
                this.cards = response.data.data;
            })
        },
    },
    watch: {
        "store.archetypeSelected": function (searchArchetype) {
            // svuota l'array di cards
            this.cards = [];
            this.fetchCards(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${searchArchetype}&num=20&offset=0`);
        }
    },
    mounted() {
        this.fetchCards();
    }
}
</script>

<template>
    <div class="container px-3 py-5">
        <div class="row row-cols-1 row-cols-md-2 row-cols-lg-5 gy-4">
            <div class="col" v-for="singleCard in cards" :key="singleCard.id">
                <Card :card="singleCard" />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.container {
    background-color: white;
    margin-top: 4rem;
    margin-bottom: 4rem;
    font-weight: bold;
}
</style>