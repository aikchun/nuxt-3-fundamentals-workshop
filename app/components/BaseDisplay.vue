<script setup>
import { defineEmits } from 'vue';
const props = defineProps({
  itemList: {
    type: Array,
    default: () => []
  },
  title: {
    type: String,
    required: true
  },
  itemType: {
    type: String,
    required: true
  },
})

const emits = defineEmits([
  'update:itemList'
])


async function fetchItemList() {

  const response = await fetch(`https://jsonplaceholder.typicode.com/${props.itemType}`);
  const json = await response.json();
  emits('update:itemList', json)
}

</script>
<template>
  <div class="section">
    <slot name="image" />
    <h1 class="title">{{ title }}</h1>
    <p>
      Photo by
      <a
        href="https://unsplash.com/@glenncarstenspeters?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Glenn
        Carstens-Peters</a>
      on
      <a
        href="https://unsplash.com/s/photos/todo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
    </p>
    <button type="button" @click="fetchItemList">Fetch</button>
    <p>
      <slot name="metrics" />
    </p>
    <ul class="list">
      <slot name="itemList" />
    </ul>
  </div>
</template>
<style></style>
