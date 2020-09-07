<template>
  <div id="app" class="container text-center">
    <TodoForm @add-todo="addTodo"></TodoForm>
    <TodoTable :todos="todos" @delete-todo="deleteTodo"></TodoTable>
  </div>
</template>

<script>
import TodoTable from './components/TodoTable.vue'
import TodoForm from './components/TodoForm.vue'
export default {
  name: 'app',
  components: {
    TodoTable,
    TodoForm
  },
  data: () => ({
    todos: []
  }),
  mounted: function() {
    this.todos = JSON.parse(localStorage.getItem('todos')) || [];
  },
  methods: {
    addTodo: function(newTodo) {
      this.todos.push(newTodo);
    },
    deleteTodo: function(id) {
      this.todos = this.todos.filter(function(todo) {
        return id !== todo.id;
      });
    }
  },
  watch: {
    todos: {
      handler: function() {
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
      deep: true
    }
  },
}
</script>