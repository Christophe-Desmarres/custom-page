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
    background-color: var(--color-background-reverse);
    padding: 1rem;
    text-align: center;
}

footer a {
    color: var(--color-text-reverse);
    text-decoration: none;
    font-size: 1.2rem;
    margin: 0 1rem;
}

footer a:hover {
    text-decoration: underline;
}



</style>