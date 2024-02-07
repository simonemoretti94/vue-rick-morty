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
            <div class="row">
                <CharacterItem v-for="character in this.characters.results" :characterEl="character"></CharacterItem>
            </div>
        </div>
    </main>
</template>

<style scoped></style>