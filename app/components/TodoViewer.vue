<script setup>
import BaseDisplay from "./BaseDisplay.vue"

const todoList = ref([])

defineProps({
  title: {
    type: String,
    default: "Hello World",
  },
});

const completedItems = computed(() => todoList.value.filter(todo => todo.completed))
const remainingItems = computed(() => todoList.value.filter(todo => !todo.completed))

</script>
<template>
  <div> Before Base Display</div>
  <BaseDisplay :title="title" itemType="todos" v-model:itemList="todoList">
    <template v-slot:metrics>
      <p>{{ completedItems.length }} Completed | {{ remainingItems.length }} Remaining</p>
    </template>
    <template v-slot:itemList>
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" />
        {{ todo.title }}
      </li>
    </template>
  </BaseDisplay>
</template>
