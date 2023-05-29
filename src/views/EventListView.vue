<script setup>
  import EventCard from '@/components/EventCard.vue';
  import Eventservice from '@/services/Eventservice.js'
  import { ref, onMounted } from 'vue'

  const events = ref(null)

  onMounted(() => {
    Eventservice.getEvents()
    .then(response => {
    events.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
  })

  
</script>

<template>
  <div class="events">
    <h1>Event for good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>