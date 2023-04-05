<template>
    <footer>
        <a href="#">home</a>
        <a href="#">about</a>
        <a href="#">contact</a>
        
    </footer>
</template>

<script>
export default {
    name: 'Footer',

}
</script>

<style scoped>

footer {
    background-color: #333;
    color: #fff;
    padding: 1rem;
    text-align: center;
}

footer a {
    color: #fff;
    text-decoration: none;
    margin: 0 1rem;
}

footer a:hover {
    text-decoration: underline;
}



</style>