<template>
  <div id="app">
    <h1>Список дел 🎉</h1>
    <TodoForm @add="addTodo" />
    <div class="filter-container">
      <label>Фильтер: </label>
      <input v-model="filterText" type="text" />
    </div>
    <TodoList :todos="todos" :filterText="filterText" @delete="deleteTodo" />
  </div>
</template>

<script>
import TodoForm from './components/TodoForm.vue';
import TodoList from './components/TodoList.vue';

export default {
  data() {
    return {
      todos: [],
      filterText: '',
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({ title: newTodo });
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
  components: {
    TodoForm,
    TodoList,
  },
};
</script>

<style>
/* New Year's theme styles */
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin: 20px;
  background-color: #f1c40f; /* Golden Yellow */
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #e74c3c; /* Red */
}

.filter-container {
  margin-bottom: 10px;
}

input {
  padding: 5px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

</style>
