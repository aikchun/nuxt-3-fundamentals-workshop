<script setup>
</script>
<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <TodoViewer title="New Todo List" />
        </div>
        <div class="column">
          <PhotoViewer>
            <template #metrics="slotProps">
              <strong>{{ slotProps.evenAlbums.length }}</strong> evenAlbums |
              {{ slotProps.oddAlbums.length }} oddAlbums
            </template>
          </PhotoViewer>
        </div>
      </div>
    </div>
  </div>
  <NuxtPage />
</template>
<style lang="scss"></style>
