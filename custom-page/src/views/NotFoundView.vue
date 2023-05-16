<template>
    <div class="not-found">
        <h1>Tu es perdu ??</h1>
        <p>Retrouve moi <router-link to="/" class="link">en cliquant ici</router-link></p>
    </div>
</template>

<script>
export default {
    name: 'NotFound',

}
</script>

<style scoped>
.not-found {
    width: auto;
    margin: 1rem auto;
    padding: 1rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 3rem;
    text-align: center;
}

.not-found p{
    margin: 2rem;
    font-size: 1.5rem;
}

.link {
    color: #000;
    text-decoration: none;
    font-weight: bold;
    padding: 0.5rem 1rem;
}

.link:hover {
    color: #000;
    text-decoration: underline;
}

.link::after {
    content: '👈';
    margin-left: 0.5rem;
}

</style>