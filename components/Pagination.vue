<template lang="html">
  <div class="button">
    <button 
      class="btn btn-info btn-sm" 
      @click="prevPage">
      &lt;
    </button>
    <button 
      class="btn btn-info btn-sm" 
      @click="nextPage">
      &gt;
    </button>
  </div>
</template>

<script>
import { eventBus } from '@/assets/EventBus'
export default {
  name: 'Pagination',
  props: {
    size: {
      type: Number,
      require: false,
      default: 12
    }
  },
  data() {
    return {
      albums: [],
      pageNumber: 0
    }
  },
  computed: {
    pageCount() {
      let l = this.albums.length
      let s = this.size
      return Math.floor(l / s)
    }
  },
  created() {
    eventBus.$on('Albums', albums => {
      this.albums = albums
      eventBus.$emit('AlbumPaginated', this.albums.slice(0, this.size))
    })
  },
  methods: {
    nextPage() {
      if (this.pageNumber < this.pageCount) {
        this.pageNumber++
      }
      this.paginatedData()
    },
    prevPage() {
      if (this.pageNumber > 0) {
        this.pageNumber--
      }
      this.paginatedData()
    },
    paginatedData() {
      const start = this.pageNumber * this.size,
        end = start + this.size
      eventBus.$emit('AlbumPaginated', this.albums.slice(start, end))
    }
  }
}
</script>

<style scoped>
.button {
  margin: 20px 0;
}
</style>
