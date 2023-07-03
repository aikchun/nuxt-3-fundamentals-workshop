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
  <div class="container">
    <div class="section">
      <h1>Photo Gallery</h1>
      <button type="button" @click="fetchPhotos">Fetch</button>
      <p>Number of Photos {{ numberOfPhotos }}</p>
      <p>
        {{ evenAlbums.length }} even albums | {{ oddAlbums.length }} odd albums
      </p>
      <ul :class="$style.photo_gallery_list">
        <li v-for="photo in photoList" :key="`photo-${photo.id}`">
          <img :src="photo.thumbnailUrl" />
        </li>
      </ul>
    </div>
  </div>
</template>
<style lang="scss" module>
@import "./node_modules/bulma/bulma.sass";
.photo_gallery_list {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}
</style>
