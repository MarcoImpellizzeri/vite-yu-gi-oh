<script>
import axios from 'axios';

export default {
    data() {
        return {
            namesOptions: []
        }
    },
    methods: {
        fatchOptionSelect() {
            const url = "https://db.ygoprodeck.com/api/v7/archetypes.php"

            axios.get(url).then((response) => {
                this.namesOptions = response.data;
            })
        }
    },
    mounted() {
        this.fatchOptionSelect();
    }
}
</script>

<template>
    <div class="container">
        <select class="form-select my-5">
            <option>Selezione l'archetipo</option>
            <option v-for="(nameOption, i) in namesOptions" :key="`'option'${i}`">
                {{ nameOption.archetype_name }}
            </option>
        </select>
    </div>
</template>

<style lang="scss" scoped>
.form-select {
    width: 20%;
    background-color: black;
    color: white;
    border: 0;
    box-shadow: none;
}
</style>