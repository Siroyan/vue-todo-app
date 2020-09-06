<template>
  <tbody>
    <tr v-for="(todo, index) in todos" :key="index">
      <Todo :todo="todo" :index="index" @delete-todo="deleteTodo"></Todo>
    </tr>
  </tbody>
</template>

<script>
import Todo from './Todo.vue'
export default {
  name: 'Todolist',
  components: {
    Todo
  },
  props: {
    todos: {

    }
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