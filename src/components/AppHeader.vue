<script>
import AppLogo from './AppLogo.vue';
import HeaderNav from './HeaderNav.vue';

export default {
    name: 'AppHeader',
    components: {
        AppLogo,
        HeaderNav,

    },
    data() {

        return {
            menu: [
                {
                    url: '#',
                    text: 'Home',
                },
                {
                    url: '#',
                    text: 'Characters',
                },
            ],
        }
    },
    methods: {

    },
}
</script>

<template>
    <header>
        <div class="container">
            <AppLogo></AppLogo>
            <nav>
                <ul>
                    <HeaderNav v-for="anchor in menu" :dataMenu="anchor"></HeaderNav>
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
                display: flex;
                list-style: none;
                gap: 1 rem;
            }

        }
    }
}
</style>