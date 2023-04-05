<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/templates/header.vue'
import Footer from './components/templates/footer.vue'



</script>

<template>
  <Header />
  <main>
    <RouterView />
  </main>
  <Footer />
</template>

<style scoped>

</style>
