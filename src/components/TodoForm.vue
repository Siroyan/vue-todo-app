<template>
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
</template>

<script>
export default {
  name: 'TodoForm',
  data: () => ({
    newTodo: {
      id: '',
      title: '',
      isDone: false
    }
  }),
  methods: {
    addTodo: function() {
      if (this.newTodo.title === '') return;
      this.newTodo.id = new Date().getTime().toString(16);
      this.$emit('add-todo', this.newTodo);
      // 空に戻しておく
      this.newTodo = {
        id: '',
        title: '',
        isDone: false
      };
    }
  }
}
</script>