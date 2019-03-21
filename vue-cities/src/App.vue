<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Cities msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Cities from './components/Cities.vue'

export default {
  name: 'app',
  components: {
    Cities
  }
}
</script>

<!-- this style doesn't have scoped unlike the one in Cities.vue -->

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
bo_dy {
  background-color: dodgerblue;
}
</style>

