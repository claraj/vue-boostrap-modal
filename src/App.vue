<template>
  <div id="app">
    <h1>Bootstrap Vue Modal Dialog</h1>
    <img alt="Vue logo" src="./assets/logo.png">
    <Favorites v-bind:userFavorites="favorites"/>
  </div>
</template>

<script>
import Favorites from './components/Favorites.vue'

export default {
  name: 'App',
  components: {
    Favorites
  },
  data() {
    return {
      // example data
      favorites: { color: 'orange', luckyNumber: 100 }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
