<template lang="html">
  <div class="container">
    <header>
      <h1>Albums de la página</h1>
    </header>
    <!--<div 
      v-for="album in albums" 
      :key="album.id">
      <h3>{{ album.title }}</h3>
    </div>-->
    <div class="card-columns">
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
