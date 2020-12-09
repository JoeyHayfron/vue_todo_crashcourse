<template>
<header>
    <h1>TodoList</h1>
    <router-link to="/">Home</router-link> | 
    <router-link to="/about">About</router-link>
</header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    header{
        background: #2D2D2D;
        text-align: center;
        padding: 10px;
        color: white;
    }

    header a{
        text-decoration: none;
        padding-right: 5px;
        color: white;
    }
</style>