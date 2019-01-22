<template>
  <div class="container">
    <header>
      <h1><strong>ID</strong> del album: {{ this.$route.params.id }}</h1>
      <h3>{{ album.title }}</h3>
      <nuxt-link to="/albums">Volver</nuxt-link>
    </header>
    <!--<div 
      v-for="photo in photos"
      :key="photo.id"
      class="">
      <img 
        :src="photo.url" 
        alt="">
    </div>-->
    
    <div class="card">
      <img :src="url">
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import env from '@/config/env'
export default {
  name: 'AlbumIdPage',
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
    let photosResponse = await axios.get(`
      ${env.endpoint}/albums/${this.$route.params.id}/photos`)
    this.photos = photosResponse.data
    this.url = this.photos[0].url
  }
}
</script>

<style scoped>
</style>
