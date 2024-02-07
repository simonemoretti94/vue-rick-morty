<script>
import axios from 'axios';
import CharacterItem from './CharacterItem.vue';

export default {
    name: 'AppMain',
    components: {
        CharacterItem,

    },
    data() {

        return {
            base_api_url: 'https://rickandmortyapi.com/api/character',
            characters: [],
            pagination_data: null,
            error: false,
        }
    },
    methods: {

    },
    mounted() {
        axios
            .get(this.base_api_url)
            .then((response) => {
                //console.log(response);
                this.characters = response.data;
                console.log('this characters: ', this.characters);
                console.log('this characters results: ', this.characters.results);
                // this.pagination_data = response.data.info;
            })
            .catch((error) => {
                //console.error(error);
                this.error = error.message;
            });
    },
    computed: {

    },
}
</script>

<template>
    <main>
        <div class="container">


            <div class="filters">
                <!-- add name filter input -->
                <input type="text" placeholder="Type a name to search">
                <!-- add a select status filter -->
                <select name="status" id="status">
                    <option value="" selected>All</option>
                    <option value="alive">Alive</option>
                    <option value="death">Death</option>
                    <option value="unknown">Unknown</option>
                </select>
            </div>

            <div class="row">
                <CharacterItem v-for="character in this.characters.results" :characterEl="character"></CharacterItem>
            </div>
        </div>
    </main>
</template>

<style scoped></style>