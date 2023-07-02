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
