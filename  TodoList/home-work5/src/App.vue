<template>
  <div id="app">
    
    <to-do-list 
    
    :task-list ="MyGoals"
    
    />
  </div>
</template>

<script>
import ToDoList from './components/ToDoList'

export default {
  name: 'App',
  components: {
    ToDoList
  },

  data() {
    return {
      MyGoals : [ 
        {
         id: 1,
         task: 'WakeUp',
         time: '07.10',
         status: null
        },

        {
         id: 2,
         task: 'have a breakfast',
         time: '08.10',
         status: null
        },

        {
         id: 3,
         task: 'Work',
         time: '09.10',
         status: null
        },
       
      ]
    }
  },
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
