<template>
  <div>
    <h1>Portada del album: {{ this.$route.params.id }}</h1>
    <img 
      :src="url" 
      alt="">
    <nuxt-link :to="`/albums/${this.$route.params.id}`">Volver</nuxt-link>
  </div>
</template>

<script>
import json from '@/data/coverAlbum.json'
export default {
  name: 'PortadaIdPage',
  data() {
    return {
      url: null
    }
  },
  created() {
    let infoAlbum = json.find(el => el.albumId == this.$route.params.id)
    this.url = '../' + infoAlbum.url
  }
}
</script>

<style scoped>
</style>
