<template>
  <div class="app">
    <main-layout>
      <the-navigation />
    </main-layout>
    <router-view />
  </div>
</template>

<script>

import MainLayout from './components/layout/MainLayout'
import TheNavigation from './components/navigation/TheNavigation.vue'

export default {
  components: {
    MainLayout,
    TheNavigation
  }
}
</script>

<style lang="scss">
.app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
