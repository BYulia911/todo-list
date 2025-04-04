<template>
  <h2>Todo List</h2>
  <hr>
  <TodoList
    v-bind:todos="todos"
  />
</template>

<script>
  import TodoList from './components/TodoList.vue';
  export default {
    name: 'app',
    data() {
      return {
        todos: [
          {number: 1, title: "Купить хлеб", completed: false},
          {number: 2, title: "Побегать", completed: false},
          {number: 3, title: "Сделать домашку", completed: false}
        ]
      }
    },
    components: {
      TodoList
    }
  }
</script>

<style scoped>
h2 {
  color: black;
  font-weight: 100;
}
</style>