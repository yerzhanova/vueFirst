<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{id + 1}}</strong>
            {{todo.title | uppercase}}
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>
<script>
    export default {
    	props:  {
    		todo: {
    		    type: Object,
                required: true
            },
            id: Number
        },
        filters: {
    	    uppercase(value){
    	        return value.toUpperCase();
            }
        }
    }
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
    }
    .rm {
        background: darkred;
        color: #fff;
        border-radius: 50%;
        font-weight: bold;
    }
    .done {
        text-decoration: line-through;
    }
    input {
        margin-right: 1rem;
    }
</style>