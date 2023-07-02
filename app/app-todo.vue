<script>
import { defineNuxtComponent } from "#app";
export default defineNuxtComponent({
  data: () => ({
    todoList: [],
  }),
  computed: {
    completedTodos() {
      return this.todoList.filter((todo) => todo.completed);
    },
    remainingTodos() {
      return this.todoList.filter((todo) => !todo.completed);
    },
  },
  methods: {
    async fetchTodos() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/todos"
      );
      this.todoList = await response.json();
    },
  },
});
</script>
<template>
  <div>
    <img src="/todo.jpg" width="500" alt="todo by Glenn Carstens-Peters" />
    <h1>Hello World</h1>

    <p>
      Photo by
      <a
        href="https://unsplash.com/@glenncarstenspeters?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
        >Glenn Carstens-Peters</a
      >
      on
      <a
        href="https://unsplash.com/s/photos/todo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
        >Unsplash</a
      >
    </p>
    <button type="button" @click="fetchTodos">Fetch</button>
    <p>
      {{ completedTodos.length }} completed items |
      {{ remainingTodos.length }} remaining items
    </p>
    <ul>
      <li v-for="todo in todoList" :key="`todo-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" />
        {{ todo.title }}
      </li>
    </ul>
  </div>
</template>
