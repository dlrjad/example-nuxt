<template lang="html">
  <div class="card card-body">
    <h3>{{ album.title }} - <strong>ID:</strong> {{ album.id }}</h3>
    <nuxt-link 
      :to="`/albums/${album.id}`" 
      class="btn btn-primary">Ver álbum</nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'AlbumCard',
  props: {
    album: {
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
h3 {
  min-height: 4em;
}
</style>
