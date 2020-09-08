<template>
  <tbody>
    <tr v-for="todo in todos" :key="todo.id">
      <td>
        <input type="checkbox" v-model="todo.isDone">
      </td>
      <td>{{todo.title}}</td>
      <td><span @click="deleteTodo(todo.id)" class="command">x</span></td>
    </tr>
  </tbody>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    todos: {}
  },
  methods: {
    deleteTodo: function(id) {
      this.$emit('delete-todo', id);
    }
  },
}
</script>

<style scoped>
.command {
  color: cornflowerblue;
  cursor: pointer;
}
</style>