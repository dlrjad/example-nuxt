<template lang="html">
  <div>
    <h1>Home</h1>
    <calendar
      :weekends="false" 
      class="calendar"/>
  </div>
</template>

<script>
import calendar from 'calendar-checker/src/components/calendar'
export default {
  name: 'IndexPage',
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
