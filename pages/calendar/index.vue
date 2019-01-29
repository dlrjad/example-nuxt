<template lang="html">
  <div class="container">
    <header>
      <h1>Calendario</h1>
    </header>
    <nuxt-link 
      :to="`/`" 
      class="btn btn-primary">Home</nuxt-link>
    <calendar
      :weekends="false" 
      class="calendar"/>
  </div>
</template>

<script>
import calendar from 'calendar-checker/src/components/calendar'
export default {
  name: 'CalendarPage',
  components: {
    calendar
  }
}
</script>

<style scoped>
.calendar {
  --primary: red;
}
</style>
