<template>
    <div>
      <td>
        <input type="checkbox" v-model="todo.isDone">
      </td>
      <td>{{todo.title}}</td>
      <td><span @click="deleteTodo(index)" class="command">x</span></td>
    </div>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    todo: {
      title: {
        type: String,
        required: true
      },
      isDone: {
        type: Boolean,
        required: true
      }
    },
    index: {
      type: Number,
      required: true
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