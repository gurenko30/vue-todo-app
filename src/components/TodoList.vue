<template>
  <div>
    <ul>
      <li v-for="(todo, index) in sortedAndFilteredTodos" :key="index">
        {{ todo.title }}
        <button @click="deleteTodo(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['todos', 'filterText'],
  computed: {
    sortedAndFilteredTodos() {
      const filtered = this.todos.filter(todo =>
        todo.title.toLowerCase().includes(this.filterText.toLowerCase())
      );
      return filtered.sort((a, b) => a.title.localeCompare(b.title));
    },
  },
  methods: {
    deleteTodo(index) {
      this.$emit('delete', index);
    },
  },
};
</script>

<style scoped>
/* Add your styles here */
ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #ddd;
  padding: 10px;
  margin-bottom: 10px;
}

button {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
