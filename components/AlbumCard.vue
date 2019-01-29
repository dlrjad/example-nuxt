<template lang="html">
  <div 
    class="card card-body col-sm-3 m-1">
    <div>
      <h3 class="text ellipsis">{{ album.title }}</h3>
    </div>
    <h4><strong>ID:</strong> {{ album.id }}</h4>
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
.text.ellipsis {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
h4 {
  min-height: 2em;
}
</style>
