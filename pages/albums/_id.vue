<template>
  <div class="container_">
    <div class="card">
      <div class="card-body">
        <header>
          <h3 class="card-title"><strong>ID</strong> del album: {{ this.$route.params.id }}</h3>
        </header>
        <h4 class="card-subtitle mb-2 text-muted">{{ album.title }}</h4>
        <nuxt-link :to="`/albums/portadas/${album.id}`">
          <img :src="url">
        </nuxt-link>
        <nuxt-link 
          to="/albums" 
          class="btn btn-primary"><span>Volver</span>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import env from '@/config/env'
import json from '@/data/coverAlbum.json'
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
.container_ {
  /*display: flex;
  justify-content: center;
  align-items: center;*/

  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.card {
  width: 26.5rem;
  display: flex;
  align-items: center;
  border-color: gray;
}
.btn.btn-primary {
  display: flex;
  margin-top: 1em;
}
.btn.btn-primary span {
  margin-left: calc(50% - 1em);
}
</style>
