<template lang="html">
  <div class="container">
    <header>
      <h1>Info del album</h1>
      <nuxt-link 
        to="/albums" 
        class="btn btn-primary"><span>Volver</span>
      </nuxt-link>
    </header>
    <InfoAlbum
      :id="$route.params.id"
      :album="album"
      :src="url"/>
  </div>
</template>

<script>
import axios from 'axios'
import env from '@/config/env'
import json from '@/data/coverAlbum.json'
import InfoAlbum from '@/components/InfoAlbum.vue'
export default {
  name: 'AlbumIdPage',
  components: {
    InfoAlbum
  },
  data() {
    return {
      album: {},
      photos: [],
      url: null
    }
  },
  /*created() {
    axios
      .get(`${env.endpoint}/albums/${this.$route.params.id}`)
      .then(albumResponse => {
        this.album = albumResponse.data
      })
    axios
      .get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
      .then(photosResponse => {
        this.photos = photosResponse.data
        this.url = this.photos[0].url
      })
  }*/
  created: async function() {
    let albumResponse = await axios.get(`
      ${env.endpoint}/albums/${this.$route.params.id}`)
    this.album = albumResponse.data

    let infoAlbum = json.find(el => el.albumId === this.album.id)
    this.url = infoAlbum.url

    /*let photosResponse = await axios.get(`
      ${env.endpoint}/albums/${this.$route.params.id}/photos`)
    this.photos = photosResponse.data
    this.url = this.photos[0].url*/
  }
}
</script>

<style scoped>
</style>
