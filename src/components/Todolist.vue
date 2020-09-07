<template>
  <tbody>
    <tr v-for="(todo, index) in todos" :key="index">
      <td>
        <input type="checkbox" v-model="todo.isDone">
      </td>
      <td>{{todo.title}}</td>
      <td><span @click="deleteTodo(index)" class="command">x</span></td>
    </tr>
  </tbody>
</template>

<script>
export default {
  name: 'Todolist',
  props: {
    todos: {}
  },
  methods: {
    deleteTodo: function(index) {
      this.$emit('delete-todo', index);
    }
  }
}
</script>

<style scoped>
.command {
  color: cornflowerblue;
  cursor: pointer;
}
</style>