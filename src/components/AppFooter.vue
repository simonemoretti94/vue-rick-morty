<script>
//import * from '';

export default {
    name: 'AppFooter',
    components: {
        //*,

    },
    data() {

        return {}
    },
    methods: {

    },
    mounted() {
        /*axios
        .get(''),
        .then((response) => {
           console.log(response);
        } )*/
    },
    computed: {

    },
}
</script>

<template>
    <footer>

        <p>
            &copy;Live 2024 Boolean rick morty live
        </p>

    </footer>
</template>

<style scoped>
footer {
    background-color: var(--rick-morty-dark);
    color: var(--rick-morty-lighter);
    padding: 2rem;
    text-align: center;
}
</style>