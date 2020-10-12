<template>
  <div id="app">
      <h1>To do application</h1>
      <hr>
      <AddTodo/>
      <ToDoList v-bind:todos="todos" @remove-todo="removeTodo"></ToDoList>
  </div>
</template>

<script>
import ToDoList from '@/components/ToDoList';
import AddTodo from '@/components/AddTodo';

export default {
  name: 'App',
  components: { ToDoList, AddTodo },
    data(){
        return {
            todos: [
                {id: 1, title: "buy bread", completed: false },
                {id: 2, title: "buy oil", completed: false },
                {id: 3, title: "buy beer", completed: false },
            ]
        }
    },
    methods: {
    	removeTodo(id) {
    		this.todos = this.todos.filter(t => t.id !== id)
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
