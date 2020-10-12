<template>
    <div>
        <ul>
            {{todos}}
            <ToDoItem v-for="todo in todos" v-bind:todo="todo"/>
        </ul>
    </div>
</template>


<script>
	import ToDoItem from '@/components/ToDoItem';
    export default {
    	props: ['todos'],
        components: {
        	ToDoItem
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