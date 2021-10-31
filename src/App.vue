<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Listado></Listado>
  </div>
</template>

<script>
import Listado from './components/Listado.vue'

export default {
  name: 'App',
  components: {
    Listado
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
