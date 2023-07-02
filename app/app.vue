<script setup>
import { computed, ref } from "vue";
const todoList = ref([]);

const completedTodos = computed(() =>
  todoList.value.filter((todo) => todo.completed)
);
const remainingTodos = computed(() =>
  todoList.value.filter((todo) => !todo.completed)
);

async function fetchTodos() {
  const response = await fetch("https://jsonplaceholder.typicode.com/todos");
  todoList.value = await response.json();
}
</script>
<template>
  <div class="section">
    <img src="/todo.jpg" width="500" alt="todo by Glenn Carstens-Peters" />
    <h1 class="title">Hello World</h1>

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
    <ul class="list">
      <li v-for="todo in todoList" :key="`todo-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" />
        {{ todo.title }}
      </li>
    </ul>
  </div>
</template>
<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
@import "./assets/main.scss";

:root {
  --text-color: #{$textColor};
}

.heading {
  color: var(--text-color);
}
.list {
  color: var(--text-color);
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
