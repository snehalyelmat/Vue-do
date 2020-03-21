<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "todo",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #cfcfcf;
  border-bottom: 2px #ffffff dotted;
  padding: 10px;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: red;
  color: white;
  padding: 0.1rem 0.25rem;
  border-radius: 50%;
  border: 0;
  float: right;
  cursor: pointer;
}
</style>