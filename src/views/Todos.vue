<template>
    <div>
        <h2>To do application</h2>
        <router-link to="/">Home</router-link>

        <AddTodo @add-todo="addTodo"/>
        <hr>
        <Loader v-if="loading"/>
        <ToDoList v-else-if="todos.length" v-bind:todos="todos" @remove-todo="removeTodo"></ToDoList>
        <p v-else>No todos></p>
    </div>
</template>

<script>
    import ToDoList from '@/components/ToDoList';
    import AddTodo from '@/components/AddTodo';
    import Home from '@/views/Home';
    import Loader from '@/components/Loader';
    export default {
        name: 'App',
        components: { ToDoList, AddTodo, Home, Loader },
        data(){
            return {
                todos: [
//                {id: 1, title: "buy bread", completed: false},
//                {id: 2, title: "buy oil", completed: false},
//                {id: 3, title: "buy beer", completed: false},
                ],
                loading: true
            }
        },
        mounted(){
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
                .then(response => response.json())
                .then(json => {
                    setTimeout(() => {
                        this.todos = json;
                        this.loading = false;
                    }, 1000);
                })
        },
        methods: {
            removeTodo(id) {
                this.todos = this.todos.filter(t => t.id !== id)
            },
            addTodo(todo){
                this.todos.push(todo);
            }
        }
    }
</script>