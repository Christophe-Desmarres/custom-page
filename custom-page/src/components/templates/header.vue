<template>
  <header>

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/customize">Customize</RouterLink>
      </nav>
    </div>
  </header>
</template>

<script>

export default {
    name: 'Header',

}
</script>

<style scoped>
header {
  line-height: 1.5;
}


nav {
  width: 100%;
  font-size: 1.2rem;
  font-weight: 600;
  text-align: center;
  margin-top: 1rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
  color: var(--v-main-color);
}

nav a:first-of-type {
  border: 0;
}

</style>
