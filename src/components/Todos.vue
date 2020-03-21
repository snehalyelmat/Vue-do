<template>
  <div class="list">
    <div v-for="todo in todos" :key="todo.id">
      <Todo v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";

export default {
  name: "Todos",
  props: ["todos"],
  components: {
    Todo
  }
};
</script>

<style scoped>
.list {
  margin: 1%;
}
</style>