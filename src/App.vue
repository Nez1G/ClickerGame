<template>
  <div id="app">
    <img id="logo" src="./assets/logo.png">
    <h1>Welcome to animal clicker game ! 🐾</h1>
    <AnimalsComp></AnimalsComp>
  </div>
</template>

<script>
import AnimalsComp from './components/Game'

export default {
  name: 'App',
  components: {
    AnimalsComp
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
