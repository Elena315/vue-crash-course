<template>
  <div id="app">
    <h1>Краткий план по изучению фронтенда</h1>
    <hr>
    <router-view/>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
export default {
  name: "app",
  data() {
    return {
      todos: [
      {id: 1, title: "День 1–8: HTML", completed:false},
      {id: 2, title: "День 9–16: CSS", completed:false},
      {id: 3, title: "День 17–24: Основы JavaScript", completed:false}
      ],
    };
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
  components: {
    TodoList,
    AddTodo
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
