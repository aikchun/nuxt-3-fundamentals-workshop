<script setup>
import { computed, ref } from "vue";
import TodoViewer from "./components/TodoViewer.vue";
import PhotoViewer from "./components/PhotoViewer.vue";
</script>
<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <TodoViewer title="New Todo List">
            <template #image>
              <img
                src="/todo.jpg"
                width="500"
                alt="todo by Glenn Carstens-Peters"
              />
            </template>
            <template #metrics="slotProps">
              <strong>{{ slotProps.completedTodos.length }}</strong> items
              completed
            </template>
          </TodoViewer>
        </div>
        <div class="column">
          <PhotoViewer />
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
@import "./assets/main.scss";
</style>
