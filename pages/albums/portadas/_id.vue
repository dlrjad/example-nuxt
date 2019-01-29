<template lang="html">
  <div class="container">
    <header>
      <h1>Información portada del album</h1>
      <nuxt-link 
        :to="`/albums/${$route.params.id}`"
        class="btn btn-primary">Volver</nuxt-link>
    </header>
    <CoverAlbum
      :id="$route.params.id"
      :src="url"
    />
  </div>
</template>

<script>
import json from '@/data/coverAlbum.json'
import CoverAlbum from '@/components/CoverAlbum'
export default {
  name: 'PortadaIdPage',
  components: {
    CoverAlbum
  },
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
