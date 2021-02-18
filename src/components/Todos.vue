<template>
  <div class="todos">
    <p class="title-todos">{{ todoProps.titleTodo }}</p>
    <div class="list-todos" v-for="todo in todoProps.todos" :key="todo.id">
      <TodoItem v-bind:todo="todo"  v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
  </div>
</template>



<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  props: {
    todoProps: {
      todos: Array,
      titleTodo: String,
    },
  },
  components: {
    TodoItem,
  },
};
</script>

<style scoped>
  .list-todos{
    background-color: gray
  }
</style>