<template>
  <div id="app">
    <loader-tpl v-if="!load"/>
    <header-tpl v-if="load"/>
    <main v-if="load">
      <RouterView />
    </main>
    <footer-tpl v-if="load" />
  </div>
</template>

<script>
import { RouterView } from 'vue-router'
import HeaderTpl from './components/templates/HeaderTpl.vue'
import FooterTpl from './components/templates/FooterTpl.vue'
import LoaderTpl from './components/templates/LoaderTpl.vue'

export default {
  name: 'App',
  components: {
    RouterView,
    HeaderTpl,
    FooterTpl,
    LoaderTpl
  },
  data() {
    return {
      load: false
    }
  },
  mounted() {
    window.addEventListener('load', 
      () => {
        this.load = true
      })
  }

}


</script>


<style scoped>
</style>
