<template>
  <div>
    <h2>Рекомендуемый распорядок:</h2>
    <router-link to="/"> Учебный план </router-link>
    <hr />

    <select v-model="filter">
      <option value="all">Все</option>
      <option value="completed">Выполненные</option>
      <option value="not-completed">Не выполненные</option>
    </select>
    <hr />
    <TodoList
      v-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>Список пуст</p>
    <AddTodo @add-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Loader from "@/components/Loader";
export default {
  name: "app",
  data() {
    return {
      todos: [
        { id: 1, title: "День 1–8: HTML", completed: false },
        { id: 2, title: "День 9–16: CSS", completed: false },
        { id: 3, title: "День 17–24: Основы JavaScript", completed: false },
        { id: 4, title: "День 25–27: jQuery", completed: false },
        { id: 5, title: "День 28–33: Адаптивный веб-дизайн", completed: false },
      ],
      filter: "all",
    };
  },
  computed: {
    filteredTodos() {
      if (this.filter === "all") {
        return this.todos;
      }
      if (this.filter === "completed") {
        return this.todos.filter((t) => t.completed);
      }
      if (this.filter === "not-completed") {
        return this.todos.filter((t) => !t.completed);
      }
    },
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
    AddTodo,
    Loader,
  },
};
</script>