<template>
  <h2>Todo List</h2>
  <AddTodo
    @add-todo="addTodo"
  />
  <hr>
  <TodoList
    v-if="todos.length"
    v-bind:todos="todos"
    @toggle-completed="toggleCompleted"
    @remove-todo="removeTodo"
  />
  <p v-else>No todos!</p>
</template>

<script>
  import TodoList from './components/TodoList.vue';
  import AddTodo from './components/AddTodo.vue';
  export default {
    name: 'app',
    data() {
      return {
        todos: JSON.parse(localStorage.getItem('todos')) || []
      }
    },
    components: {
      TodoList,
      AddTodo
    },
    methods: {
      toggleCompleted(id) {
        const todo = this.todos.find(t => t.id === id);
        if (todo) {
          todo.completed = !todo.completed;
          this.updateLocalStorage();
        }
      },
      removeTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
        this.updateLocalStorage();
      },
      addTodo(todo) {
        this.todos.push(todo);
        this.updateLocalStorage();
      },
      updateLocalStorage() {
        localStorage.setItem('todos', JSON.stringify(this.todos));
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