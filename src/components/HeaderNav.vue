<script>


export default {
    name: 'HeaderNav',
    props: {
        dataMenu: Object,
    }
}
</script>

<template>
    <li><a :href="dataMenu.url">{{ dataMenu.text }}</a></li>
</template>

<style scoped>
a {
    margin: auto .5rem;
    text-decoration: none;
    color: var(--rick-morty-dark);
}
</style>