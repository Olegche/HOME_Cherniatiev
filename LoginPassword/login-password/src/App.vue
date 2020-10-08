<template>
  <div id="app">
    <login-password 
    :user-list ="userList"
  
    />
  </div>
</template>

<script>


import LoginPassword from './components/LoginPassword'
import userList from './usersArray'



export default {
  name: 'App',
  components: {
   LoginPassword,
   
  
  },

  data() {
    return {
      userList,
      

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
