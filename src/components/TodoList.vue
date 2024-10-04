<script>
import TodoItem from "./TodoItem.vue";
let id = 0;
export default {
  data() {
    return {
      todos: [],
    };
  },
  components: {
    TodoItem,
  },
  computed: {
    renderTodos() {
      return this.todos;
    },
  },
  methods: {
    addTodo(e) {
      const content = e.target.value.trim();

      if (content === "") {
        return;
      }

      this.todos.unshift({
        id: id++,
        content: content,
      });

      e.target.value = "";
    },
    removeTodo(id) {
      this.todos.splice(
        this.todos.findIndex((todo) => id === todo.id),
        1
      );
    },
  },
};
</script>

<template>
  <section class="real-app">
    <input
      type="text"
      class="add-input"
      @keyup.enter="addTodo"
      autofocus="autofocus"
    />
    <TodoItem
      v-for="todo in renderTodos"
      :todo="todo"
      :key="todo.id"
      @rem="removeTodo"
    />
  </section>
</template>

<style scoped>
.add-input {
  background-color: inherit;
  border: none;
  font-size: 20px;
  border-bottom: 1px solid #fff;
  color: #fff;
  padding: 20px;
  width: 400px;
}

.real-app {
  padding: 20px;
  width: 600px;
  margin: 0, auto;
  box-shadow: 0 0 5px #666;
}
</style>
