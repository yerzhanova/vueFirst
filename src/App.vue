<template>
  <div id="app">
      <h1>To do application</h1>
      <hr>
      <ToDoList v-bind:todos="todos"></ToDoList>
  </div>
</template>

<script>
import ToDoList from '@/components/ToDoList';
export default {
  name: 'App',
  components: {
  	ToDoList
  },
    data(){
        return {
            todos: [
                {id: 1, title: "buy bread", completed: false },
                {id: 2, title: "buy oil", completed: false },
                {id: 3, title: "buy beer", completed: false },
            ]
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
