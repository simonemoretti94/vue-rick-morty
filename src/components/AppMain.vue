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
            loading: true,
            searchText: '',
            selectedStatus: '',
        }
    },
    computed: {
        getResults() {
            return this.characters.results ? this.characters.results.length : 'No results yet';
        },

        loadingResult() {
            return this.loading == false ? '' : ', loading...';
        }
    },
    methods: {
        getCharacters(url) {
            axios
                .get(url)
                .then((response) => {
                    //console.log(response);
                    this.characters = response.data;
                    console.log('this characters: ', this.characters);
                    console.log('this characters results: ', this.characters.results);
                    this.loading = !this.loading;
                    // this.pagination_data = response.data.info;
                })
                .catch((error) => {
                    //console.error(error);
                    this.error = error.message;
                });
        },
        filterResults() {
            const url = `${this.base_api_url}?name=${this.searchText}&status=${this.selectedStatus}`;
            console.log(url);

            this.getCharacters(url);
        },
    },
    created() {
        // setTimeout(() => {
        //     this.getCharacters(this.base_api_url);
        // }, 5000);
        this.getCharacters(this.base_api_url);
    },
}
</script>

<template>
    <main>
        <div class="container">


            <div id="main_filters">
                <!-- add name filter input -->
                <input type="text" placeholder="Type a name to search" v-model="searchText">
                <!-- add a select status filter -->
                <select name="status" id="status" v-model="selectedStatus">
                    <option value="" selected>All</option>
                    <option value="Alive">Alive</option>
                    <option value="Dead">Dead</option>
                    <option value="Unknown">Unknown</option>
                </select>

                <button @click="filterResults">Filter</button>
            </div>

            <div v-if="!loading" class="row">
                <CharacterItem v-for="character in this.characters.results" :characterEl="character"></CharacterItem>
            </div>
            <div id="v-else" v-else>
                <div style="display: flex; justify-content: center;">
                    <i class="fa-solid fa-spinner fa-spin"></i>
                    <div id="results" class="my-1">{{ getResults }}{{ loadingResult }}</div>
                </div>
            </div>


        </div>
    </main>
</template>

<style scoped>
div#main_filters {
    margin: .5rem auto;

    >input,
    select {
        border-radius: 5px;
        text-align: center;
    }
}

div#results {
    margin: .5rem auto;
}

div#v-else {
    display: flex;

    >i {
        margin: 0;
        padding: 0;
    }

    >div {
        align-self: flex-start;
    }
}
</style>