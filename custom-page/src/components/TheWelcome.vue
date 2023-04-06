<template>
  <div class="home">
    <hello-world msg="Bienvenue" class="titre"/>
    <img alt="Vue logo" :src="logo" class="logo"/>

  </div>
</template>

<script>
import HelloWorld from './HelloWorld.vue';
import logo from '../assets/logo.svg';

export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
  data() {
    return {
      logo,
    };
  },

}
</script>

<style scoped>

.logo {
  height: 1.5em;
}

</style>