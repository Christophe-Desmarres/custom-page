<template>
  <div class="home">
    <hello-world msg="Bienvenue" class="titre"/>
  </div>
</template>

<script>
import HelloWorld from './HelloWorld.vue';

export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
}
</script>

<style scoped>

.logo {
  height: 1.5em;
}

</style>