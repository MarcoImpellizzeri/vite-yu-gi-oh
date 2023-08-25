<script>
export default {
    props: {
        card: {
            type: Object,
            required: true,
        }
    }
}
</script>

<template>
    <div class="card">
        <img :src="card.card_images[0].image_url" class="card-img-top" alt="card img">
        <div class="card-body text-center d-flex flex-column">
            <h5 class="card-title mb-3">{{ card.name }}</h5>
            <p class="card-text mt-auto">{{ card.archetype }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    height: 100%;
    background-color: orange;
    color: white;

    p {
        color: black;
    }
}
</style>