<template lang="html">
  <div class="container">
    <header>
      <h1>Albums de la página</h1>
      <nuxt-link 
        :to="`/`" 
        class="btn btn-primary">Home</nuxt-link>
    </header>
    <div class="row justify-content-around">
      <AlbumCard
        v-for="album in albums"
        :album="album" 
        :key="album.id" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import env from '@/config/env'
import AlbumCard from '@/components/AlbumCard'
export default {
  name: 'IndexPage',
  components: {
    AlbumCard
  },
  data() {
    return {
      albums: []
    }
  },
  created() {
    axios.get(`${env.endpoint}/albums`).then(response => {
      this.albums = response.data
    })
  }
}
</script>

<style scoped>
</style>
