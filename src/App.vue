<script>
import TheHeader from './components/TheHeader.vue';
import CardsList from './components/CardsList.vue';

export default {
    components: {
        TheHeader,
        CardsList
    }
}
</script>

<template>
    <TheHeader />
    <main>
        <CardsList />
    </main>
</template>

<style lang="scss"></style>
