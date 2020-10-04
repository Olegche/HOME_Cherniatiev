<template>
  <div id="app">
   
    <money-bank
    />
    <br>
    
    <money-bank2
    />
    
  </div>
</template>

<script>

import MoneyBank from './components/MoneyBank'
import MoneyBank2 from './components/MoneyBank2'


export default {
  name: 'App',
  components: {
    MoneyBank,
    MoneyBank2

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
