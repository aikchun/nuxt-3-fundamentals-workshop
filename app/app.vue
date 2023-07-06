<script setup>
// import TodoViewer from "./components/TodoViewer.vue";
// import PhotoViewer from "./components/PhotoViewer.vue";
</script>
<template>
  <!-- <div class="container"> -->
  <!--   <div class="section"> -->
  <!--     <div class="columns"> -->
  <!--       <div class="column"> -->
  <!--         <TodoViewer title="New Todo List" /> -->
  <!--       </div> -->
  <!--       <div class="column"> -->
  <!--         <PhotoViewer> -->
  <!--           <template #metrics="slotProps"> -->
  <!--             <strong>{{ slotProps.evenAlbums.length }}</strong> evenAlbums | -->
  <!--             {{ slotProps.oddAlbums.length }} oddAlbums -->
  <!--           </template> -->
  <!--         </PhotoViewer> -->
  <!--       </div> -->
  <!--     </div> -->
  <!--   </div> -->
  <!-- </div> -->
  <TheNavBar />
  <NuxtPage />
</template>
<style lang="scss">
@import "./node_modules/bulma/bulma.sass";
@import "./assets/main.scss";
</style>
