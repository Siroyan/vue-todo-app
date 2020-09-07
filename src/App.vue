<template>
  <div id="app" class="container text-center">
    <TodoForm @add-todo="addTodo"></TodoForm>
    <Todolist :todos="todos" @delete-todo="deleteTodo"></Todolist>
  </div>
</template>

<script>
import Todolist from './components/Todolist.vue'
import TodoForm from './components/TodoForm.vue'
export default {
  name: 'app',
  components: {
    Todolist,
    TodoForm
  },
  data: () => ({
    todos: []
  }),
  methods: {
    addTodo: function(newTodo) {
      this.todos.push(newTodo);
    },
    deleteTodo: function(id) {
      this.todos = this.todos.filter(function(todo) {
        return id !== todo.id;
      });
    }
  }
}
</script>