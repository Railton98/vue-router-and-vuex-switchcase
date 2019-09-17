<template>
  <div class id="app">
    <router-view />
  </div>
</template>

<script>
import Todo from "./components/Todo";

export default {
  name: "app",
  components: { Todo },
  data() {
    return { todos: [], todo: { checked: false } };
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked: false };
    },

    toggleTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id);
      if (index > -1) {
        const checked = !this.todos[index].checked;
        this.$set(this.todos, index, { ...this.todos[index], checked });
      }
    },

    removeTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id);
      if (index > -1) {
        this.$delete(this.todos, index);
      }
    }
  }
};
</script>

<style scoped>
.img-logo {
  max-width: 200px;
  margin: 0 auto;
}

.todo-list {
  padding-top: 2rem;
}
</style>

