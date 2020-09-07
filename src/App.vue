<template>
  <div id="app" class="container text-center">
    <div>
      <form class="row" @submit.prevent="addTodo">
        <!-- やることタイトル -->
        <div class="form-group col-10">
          <input type="text" class="form-control" id="todo-title" placeholder="やること" v-model="newTodo.title">
        </div>
        <!-- 登録ボタン -->
        <div class="form-group col-2">
          <button type="submit" class="btn btn-primary">登録</button>
        </div>
      </form>
    </div>

    <!-- やることリスト -->
    <div>
      <table class="table">
        <thead>
          <tr>
            <th scope="col">状態</th>
            <th scope="col">タイトル</th>
            <th scope="col">削除</th>
          </tr>
        </thead>
        <Todolist :todos="todos" @delete-todo="deleteTodo"></Todolist>
      </table>
    </div>
  </div>
</template>

<script>
import Todolist from './components/Todolist.vue'
export default {
  name: 'app',
  components: {
    Todolist
  },
  data: () => ({
    newTodo: {
      id: '',
      title: '',
      isDone: false
    },
    todos: []
  }),
  methods: {
    addTodo: function() {
      if (this.newTodo.title === '') return;
      let item = {
        id: new Date().getTime().toString(16),
        title: this.newTodo.title,
        isDone: this.newTodo.isDone
      };
      // リストに追加
      this.todos.push(item);
      // 空に戻しておく
      this.newTodo = {
        id: '',
        title: '',
        isDone: false
      };
    },
    deleteTodo: function(id) {
      this.todos = this.todos.filter(function(todo) {
        return id !== todo.id;
      });
    }
  }
}
</script>

<style scoped>

</style>
