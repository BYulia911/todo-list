<template>
    <div>
        <ul>
            <TodoItem
            v-for="todo of todos"
            v-bind:todo="todo"
            v-on:remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
    props: {
        todos: {
            type: Array,
            required: true
        }
    },
    components: {
        TodoItem
    },
    methods: {
        removeTodo (id) {
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
    display: flex;
    flex-direction: column;
}
</style>