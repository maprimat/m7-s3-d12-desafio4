<!-- TEMPLATE -->
<template>
    <NavbarComp />
    <router-view />
</template>

<!-- SCRIPT -->
<script>
import NavbarComp from '@/components/NavbarComp.vue'

export default {
    name: "App",
    components: {
        NavbarComp
    },
}
</script>

<!-- STYLE -->
<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
}
</style>
