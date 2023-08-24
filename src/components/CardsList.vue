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
        <div class="row row-cols-1 row-cols-md-2 row-cols-lg-5 gy-4">
            <div class="col" v-for="card in cards" :key="card.id">
                <div class="card">
                    <img :src="card.card_images[0].image_url" class="card-img-top" alt="card img">
                    <div class="card-body text-center">
                        <h5 class="card-title">{{ card.name }}</h5>
                        <p class="card-text">{{ card.archetype }}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>