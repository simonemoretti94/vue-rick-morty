<script>

export default {
    name: 'CharacterItem',
    components: {
        //*,

    },
    props: {
        characterEl: Object,
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
    <div class="col-12 col-sm-6 col-md-4 col-lg-4 col-xl-4 col-xxl-4">
        <div class="card">
            <img :src="characterEl.image" alt="">
            <div>
                {{ characterEl.name }}
                {{ characterEl.species }}
                {{ characterEl.status }}
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    background-color: #a9d3e9af;
    transition: all .3s;

    &:hover {
        filter: drop-shadow(0 0 15px #a9d3e9);
        scale: 1.01;

        >img {
            border-radius: 10px;
        }
    }

    >img {
        width: 100%;
        filter: saturate(120%) contrast(130%);
    }

    >div {
        padding: 1rem;
    }
}
</style>