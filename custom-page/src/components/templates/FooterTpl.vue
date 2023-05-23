<template>
    <footer>
        <a href="#" aria-current="page">home</a>
        <a href="#" aria-current="page">contact</a>
        
    </footer>
</template>

<script>
export default {
    name: 'FooterTpl',

}
</script>

<style scoped>

footer {
    background-color: var(--color-background-reverse);
    padding: 1rem;
    text-align: center;
    z-index: 100;
}

footer a {
    color: var(--color-text-reverse);
    text-decoration: none;
    font-size: 1.2rem;
    margin: 0 1rem;
    
}

footer a:hover {
    text-decoration: underline;
    cursor: not-allowed;
    opacity: 0.5;
    text-decoration: none;
    text-decoration: line-through;
    text-decoration-thickness: 0.2rem;
}



</style>