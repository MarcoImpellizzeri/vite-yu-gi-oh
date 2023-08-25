<script>
import axios from 'axios';
import { store } from '../store'

export default {
    data() {
        return {
            namesOptions: [],
            store,
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
        <select class="form-select my-5" v-model="store.archetypeSelected">
            <option v-for="(nameOption, i) in namesOptions" :key="`'nameOption'${i}`" :value="nameOption.archetype_name">
                {{ nameOption.archetype_name }}
            </option>
        </select>
    </div>
</template>

<style lang="scss" scoped>
.form-select {
    width: 0;
    min-width: 300px;
    background-color: black;
    color: white;
    border: 0;
    box-shadow: none;
    padding: .7rem;
}
</style>