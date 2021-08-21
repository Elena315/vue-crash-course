<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed" />
      <!-- <strong>{{ todo.id }}</strong> -->
      {{ todo.title }}
    </span>
    <button class="rm" 
    v-on:click="$emit('remove-todo', todo.id)"> &times;</button>
  </li>
</template>

<script>
import TodoItem from "@/components/TodoItem";
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
  },
};
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
  padding: 0.5rem 2rem;
}
.rm {
  background: red;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
}
input {
  margin-right: 1rem;
}
.done {
  text-decoration: line-through;
}
</style>
