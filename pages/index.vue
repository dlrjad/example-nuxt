<template lang="html">
  <div class="container">
    <header>
      <h1>Home</h1>
    </header>
    <nuxt-link 
      :to="`/albums/`" 
      class="btn btn-primary">Ver los albumns</nuxt-link>
    <nuxt-link
      :to="`./calendar`" 
      class="btn btn-primary">Calendario</nuxt-link>
    <nuxt-link
      :to="`./about`" 
      class="btn btn-primary">About</nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>

<style scoped>
.btn.btn-primary {
  display: flex;
  flex-direction: column;
  width: 10em;
  margin: 5px 0;
}
</style>
