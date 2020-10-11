<template>
  <div id="app">

<main-restaurant />
    
  </div>
</template>

<script>
import MainRestaurant from './components/MainRestaurant'

export default {
  name: 'App',
  components: {
    MainRestaurant,

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
