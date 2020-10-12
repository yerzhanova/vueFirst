<template>
    <li>
        <!--{{todo.title}}-->
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox">
            <strong>{{todo.id}}</strong>
            {{todo.title}}
        </span>
        <button class="rm">&times;</button>
    </li>
</template>
<script>
    export default {
    	props:  [{
    		todo: Object,
            required: true
        }]
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