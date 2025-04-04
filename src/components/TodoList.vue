<template>
    <div>
        <ul>
            <TodoItem
            v-for="todo of todos"
            v-bind:todo="todo"
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
    props: ['todos'],
    components: {
        TodoItem
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