<template>
  <div>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" type="text" placeholder="Добавь новое дело" />
      <button type="submit">Добавить</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
    };
  },
  methods: {
    addTodo() {
      this.$emit('add', this.newTodo);
      this.newTodo = '';
    },
  },
};
</script>

<style scoped>
/* New Year's theme styles */
form {
  margin-bottom: 20px;
}

input[type="text"] {
  padding: 5px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  background-color: #27ae60;
  color: white;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
  border-radius: 4px;
}

</style>
