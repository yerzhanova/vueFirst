<template>
    <div>
        <ul>
            <ToDoItem v-for="(todo, i) in todos" v-bind:todo="todo" v-bind:id="i" v-on:remove-todo="removeTodo"/>
        </ul>
    </div>
</template>


<script>
	import ToDoItem from '@/components/ToDoItem';
    export default {
    	props: ['todos'],
        components: {
        	ToDoItem
        },
        methods: {
    		removeTodo(id){
    			console.log(id);
    			this.$emit('remove-todo', id);
            }
        }
	}
</script>
<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }

</style>