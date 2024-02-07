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

            <AppLogo></AppLogo>
            <nav>
                <ul>
                    <li><a href="">Home</a></li>
                    <li><a href="">Characters</a></li>
                </ul>
            </nav>

        </div>
    </header>
</template>

<style scoped>
header {
    background-color: var(--rick-morty-lighter);
    padding: 1rem;

    >.container {
        display: flex;
        justify-content: space-between;

        >nav {
            >ul {
                list-style: none;
                display: flex;
                gap: 1 rem;
            }

            & a {
                margin: auto .5rem;
                text-decoration: none;
                color: var(--rick-morty-dark);
            }
        }


    }
}
</style>