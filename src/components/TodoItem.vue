<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <input
      type="checkbox"
      v-on:change="markComplete"
      v-model="todo.completed"
    />
    {{ todo.title }}
    <button @click="$emit('del-todo', todo.id)" class="del">x</button>
  </div>
</template>


<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object,
  },
  methods: {
    markComplete() {
      console.log('Privet')
    },
  },
};
</script>

<style scoped>
.todo-component {
  border: 1px solid black;
}

.is-complete {
  text-decoration: line-through;
}
</style>