<template>
  <div>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add todo..." />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid"; // comment this when using a RESTApi

export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: uuidv4(), // comment this when using a RESTApi
        title: this.title,
        completed: false
      };

      this.$emit("add-todo", newTodo);

      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 10px;
}

input[type="submit"] {
  flex: 2;
}
</style>