<script>
import axios from 'axios';

export default {
    data() {
        return {
            cards: []
        }
    },
    methods: {
        fetchCards() {
            const url = "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0"

            axios.get(url).then((response) => {
                this.cards = response.data.data;
            })
        }
    },
    mounted() {
        this.fetchCards();
    }
}
</script>

<template>
    <div class="container">
        <div class="row row-cols-1 row-cols-md-2 row-cols-lg-5">
            <div class="col" v-for="card in cards" :key="card.id">
                <div class="card">
                    <img :src="card." class="card-img-top" alt="">
                    <div class="card-body">
                        <h5 class="card-title"></h5>
                        <p class="card-text"></p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>