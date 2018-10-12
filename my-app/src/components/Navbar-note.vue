<template>
    <header>
        <a class="navbar-brand" href="#">A P P</a>
    </header>
</template>

<script>
    export default {
        name: "Header"
    }
</script>

<style scoped>
    header{
        display: flex;
        flex-direction: row;
        justify-content: center;
        background-color: #f9f8f6;
    }

    .navbar-brand{
        color: black;
    }
</style>