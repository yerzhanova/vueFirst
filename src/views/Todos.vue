<template>
    <div>
        <h2>To do application</h2>
        <router-link to="/">Home</router-link>

        <AddTodo @add-todo="addTodo"/>
        <hr>
        <select v-model="filter">
            <option value="all">All</option>
            <option value="completed">Completed</option>
            <option value="not-completed">Not completed</option>
        </select>
        <Loader v-if="loading"/>
        <ToDoList v-else-if="filteredTodos.length" v-bind:todos="filteredTodos" @remove-todo="removeTodo"></ToDoList>
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
                loading: true,
                filter: 'all'
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
        computed: {
            filteredTodos() {
                if (this.filter === 'all') {
                    return this.todos;
                }

                if (this.filter === 'completed') {
                    return this.todos.filter(t => t.completed);
                }

                if (this.filter === 'not-completed') {
                    return this.todos.filter(t => !t.completed);
                }
            }
        },
//        watch: {
//            filter(value){
//                console.log(value)
//            }
//        },
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