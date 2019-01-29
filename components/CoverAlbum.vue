<template lang="html">
  <div>
    <h3>Portada del album: {{ id }}</h3>
    <img 
      :src="src"
      class="cover"
      alt="">
  </div>
</template>

<script>
export default {
  name: 'CoverAlbum',
  props: {
    id: {
      type: String,
      default: null
    },
    src: {
      type: String,
      default: null
    }
  }
}
</script>

<style scoped>
</style>
