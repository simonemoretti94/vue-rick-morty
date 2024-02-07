<script>
import axios from 'axios';

export default {
    name: 'AppMain',
    components: {
        //*,

    },
    data() {

        return {
            base_api_url: 'https://rickandmortyapi.com/api/character',
            characters: null,
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
    <div v-if="characters">
        <div v-for="(character) in this.characters.results" :key="character.id + '_character '" class="">
            {{ character.name }}
            <img :src="character.image" alt="">
            {{ character.species }}
            {{ character.status }}
            <br>
        </div>
    </div>
    <div v-else>
        <p>Ciao zi</p>
    </div>
</template>

<style scoped></style>