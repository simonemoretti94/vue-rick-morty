<script>
import AppLogo from './AppLogo.vue';

export default {
    name: 'AppHeader',
    components: {
        AppLogo,

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
    <header>
        <div class="container">
            <div class="logo">
                <AppLogo></AppLogo>
            </div>
        </div>
    </header>
</template>

<style scoped></style>