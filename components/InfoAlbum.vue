<template>
  <div class="container_">
    <div class="card">
      <div class="card-body">
        <h3 class="card-title"><strong>ID</strong> del album: {{ this.$route.params.id }}</h3>
        <h4 class="card-subtitle mb-2 text-muted">{{ album.title }}</h4>
        <nuxt-link :to="`/albums/portadas/${album.id}`">
          <img :src="src">
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InfoAlbum',
  props: {
    album: {
      type: Object,
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
</style>
