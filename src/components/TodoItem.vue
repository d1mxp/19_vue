<script>
export default {
  methods: {
    removeTodo() {
      this.$emit("rem", this.todo.id);
    },
  },
  props: {
    todo: {
      type: Object,
    },
  },
};
</script>

<template>
  <div class="todo-item">
    <span>{{ todo.content }}</span>
    <button @click="removeTodo">Del</button>
  </div>
</template>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  margin: 20px 0;
}
</style>
