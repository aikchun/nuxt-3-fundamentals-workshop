<script>
import { defineNuxtComponent } from "#app";
export default defineNuxtComponent({
  data: () => ({
    photoList: [],
  }),
  computed: {
    numberOfPhotos() {
      return this.photoList.length;
    },
  },
  methods: {
    async fetchPhotos() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/photos"
      );
      this.photoList = await response.json();
    },
  },
  created() {
    this.fetchPhotos();
  },
});
</script>
<template>
  <div>
    <h1>Photo Gallery</h1>
    <p>Number of Photos {{ numberOfPhotos }}</p>
    <ul>
      <li v-for="photo in photoList" :key="`photo-${photo.id}`">
        <img :src="photo.thumbnailUrl" />
        {{ photo.title }}
      </li>
    </ul>
  </div>
</template>
