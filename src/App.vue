<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layouts/Header";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      // uncomment this when using a RESTApi
      // axios
      //   .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      //   .then(
      //     res =>
      //       (this.todos = this.todos.filter(todo => todo.id !== id, res.data))
      //   )
      //   .catch(err => console.log(err));

      this.todos = this.todos.filter(todo => todo.id !== id); // comment this when using a RESTApi
    },
    addTodo(newTodo) {
      // uncomment this when using a RESTApi
      // const { title, completed } = newTodo;

      // axios
      //   .post("https://jsonplaceholder.typicode.com/todos", {
      //     title,
      //     completed
      //   })
      //   .then(res => (this.todos = [...this.todos, res.data]))
      //   .catch(err => console.log(err));

      this.todos = [...this.todos, newTodo]; // comment this when using a RESTApi
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then(res => (this.todos = res.data))
      .catch(err => console.log(err));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
