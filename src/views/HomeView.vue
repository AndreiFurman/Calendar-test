<template>
  <div class="main-calendar">
    <h1>Calendar</h1>
    <div class="calendar-holder">
    <Calendar></Calendar>
    </div>
  </div>
</template>

<script>

import Calendar from '@/components/Calendar.vue'

export default {
  name: 'HomeView',
  components: {
    Calendar
  }
}
</script>
<style>
.main-calendar{
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.calendar-holder{
  max-width: 400px;
}
</style>
