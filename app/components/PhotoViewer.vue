<script setup>
import { computed, ref } from "vue";
const photoList = ref([]);
const numberOfPhotos = computed(() => photoList.value.length);

const evenAlbums = computed(() =>
  photoList.value.filter((photo) => photo.albumId % 2 === 0)
);

const oddAlbums = computed(() =>
  photoList.value.filter((photo) => !(photo.albumId % 2 === 0))
);

async function fetchPhotos() {
  const response = await fetch("https://jsonplaceholder.typicode.com/photos");
  photoList.value = await response.json();
}
</script>
<template>
  <h1>Photo Gallery</h1>
  <button type="button" @click="fetchPhotos">Fetch</button>
  <p>Number of Photos {{ numberOfPhotos }}</p>
  <p>{{ evenAlbums.length }} even albums | {{ oddAlbums.length }} odd albums</p>
  <ul :class="$style.list">
    <li v-for="photo in photoList" :key="`photo-${photo.id}`">
      <img :src="photo.thumbnailUrl" />
    </li>
  </ul>
</template>
<style module>
.list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
