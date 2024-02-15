<script>
import axios from 'axios';
import CharacterItem from './CharacterItem.vue';
import ResultsFilter from './ResultsFilter.vue'

export default {
    name: 'AppMain',
    components: {
        CharacterItem,
        ResultsFilter,

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
                    this.loading = false;
                    this.error = false;
                    // this.pagination_data = response.data.info;
                })
                .catch((error) => {
                    //console.error(error);
                    this.error = error.response.data.error;
                });
        },
        filterResults(data) {
            console.log('filtered', data);
            [this.searchText, this.selectedStatus] = data;
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




            <ResultsFilter @filtered="filterResults"></ResultsFilter>

            <div v-if="error" style="color: red;">{{ error }}</div>

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