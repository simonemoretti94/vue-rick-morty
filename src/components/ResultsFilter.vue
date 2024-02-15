<script>
//import * from '';

export default {
    name: 'ResultsFilter',
    emits: ['filtered'],
    data() { //variables, bool, array, objects and so on

        return {

            searchText: '',
            selectedStatus: '',
        }
    },
    methods: { //functions; all kind of manipulations
        filterResults() {
            console.log(this.searchText);
            console.log(this.selectedStatus);
            this.$emit('filtered', [this.searchText, this.selectedStatus]);
        }
    },
}
</script>

<template>
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

        <!-- <button @click="filterResults()">Filter</button> -->
        <button @click="$emit('filtered', [searchText, selectedStatus])">Filter</button>
    </div>
</template>

<style scoped></style>