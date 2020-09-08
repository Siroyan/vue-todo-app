<template>
<table class="table">
  <thead>
    <tr>
      <th scope="col">状態</th>
      <th scope="col">タイトル</th>
      <th scope="col">削除</th>
    </tr>
  </thead>
  <TodoList :todos="remaining" @delete-todo="deleteTodo"></TodoList>
  <TodoList :todos="completed" @delete-todo="deleteTodo"></TodoList>
</table>
</template>

<script>
import TodoList from './TodoList.vue'
export default {
  name: 'TodoTable',
  components: {
    TodoList
  },
  props: {
    todos: {}
  },
  methods: {
    deleteTodo: function(id) {
      this.$emit('delete-todo', id);
    }
  },
  computed: {
    remaining: function() {
      return this.todos.filter(function(todo) {
        return !todo.isDone;
      });
    },
    completed: function() {
      return this.todos.filter(function(todo) {
        return todo.isDone;
      });
    },
  }
}
</script>