<template lang="html">
  <div class="container">
    <header>
      <h1>Albums de la página</h1>
      <nuxt-link 
        :to="`/`" 
        class="btn btn-primary">Home</nuxt-link>
    </header>
    <div class="center">
      <div class="row justify-content-around">
        <AlbumCard 
          v-for="album in albums_" 
          :album="album" 
          :key="album.id" />
      </div>
      <Pagination
        :albums="albums" />
    </div>    
  </div>
</template>

<script>
import axios from 'axios'
import env from '@/config/env'
import AlbumCard from '@/components/AlbumCard'
import Pagination from '@/components/Pagination'
import { eventBus } from '@/assets/EventBus'
export default {
  name: 'IndexPage',
  components: {
    AlbumCard,
    Pagination
  },
  data() {
    return {
      albums: [],
      albums_: []
    }
  },
  created() {
    axios.get(`${env.endpoint}/albums`).then(response => {
      this.albums = response.data
      eventBus.$emit('Albums', this.albums)
    })
    eventBus.$on('AlbumPaginated', albums => {
      this.albums_ = albums
    })
  }
}
</script>

<style scoped>
.center {
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
