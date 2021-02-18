<template>
  <div id="home">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todoProps="todoProps" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todoProps: {
        todos: [],
        titleTodo: "Todos item list:",
      },
    };
  },
  methods: {
    deleteTodo(id) {
      //delete data without axios: 
      // this.todoProps.todos = this.todoProps.todos.filter(
      //   (item) => item.id !== id);

      //with axios:
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.todoProps.todos = this.todoProps.todos.filter(item => item.id !== id))
      .catch(err => console.error(err));
    },
    addTodo(newTodo) {
      //added data from input without axios: 
      // this.todoProps.todos = [...this.todoProps.todos, newTodo];

      //wth axios:
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then(
          (res) => (this.todoProps.todos = [...this.todoProps.todos, res.data])
        )
        .catch((err) => console.error(err.message));
    },
  },
  created() {
    const url = "https://jsonplaceholder.typicode.com/todos?_limit=5";
    axios
      .get(url)
      .then((res) => (this.todoProps.todos = res.data))
      .catch((err) => console.error(err.message));
  },
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
.btn {
  display: inline-block;
  border: none;
  color: white;
  background: #555;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>



