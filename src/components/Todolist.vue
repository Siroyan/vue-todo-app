<template>
<table class="table">
  <thead>
    <tr>
      <th scope="col">状態</th>
      <th scope="col">タイトル</th>
      <th scope="col">削除</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(todo, index) in todos" :key="index">
      <td>
        <input type="checkbox" v-model="todo.isDone">
      </td>
      <td>{{todo.title}}</td>
      <td><span @click="deleteTodo(todo.id)" class="command">x</span></td>
    </tr>
  </tbody>
</table>
</template>

<script>
export default {
  name: 'Todolist',
  props: {
    todos: {}
  },
  methods: {
    deleteTodo: function(id) {
      this.$emit('delete-todo', id);
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