<template>
  <h2>Todo List</h2>
  <AddTodo
    @add-todo="addTodo"
  />
  <hr>
  <TodoList
    v-bind:todos="todos"
    @remove-todo="removeTodo"
  />
</template>

<script>
  import TodoList from './components/TodoList.vue';
  import AddTodo from './components/AddTodo.vue';
  export default {
    name: 'app',
    data() {
      return {
        todos: [
          {id: 1, title: "Купить хлеб", completed: false},
          {id: 2, title: "Побегать", completed: false},
          {id: 3, title: "Сделать домашку", completed: false}
        ]
      }
    },
    components: {
      TodoList,
      AddTodo
    },
    methods: {
      removeTodo (id) {
        this.todos = this.todos.filter(t => t.id != id);
      },
      addTodo (todo) {
        this.todos.push(todo);
      }
    }
  }
</script>

<style scoped>
h2 {
  color: black;
  font-weight: 100;
}
</style>