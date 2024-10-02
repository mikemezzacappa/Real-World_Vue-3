<script setup>
import EventCard from '@/components/EventCard.vue'
// import { ref } from 'vue'
// import Flipbook from 'flipbook-vue'
// import img1 from '@/assets/pages/1.jpg'
// import img2 from '@/assets/pages/2.jpg'
// import img3 from '@/assets/pages/3.jpg'
// import img4 from '@/assets/pages/4.jpg'
// import { onMounted } from 'vue'
import { ref, onMounted } from 'vue'
import EventServices from '@/services/EventServices';
// import $ from 'jquery'
const events = ref(null)
/*
const events = ref([
  {
    id: 5928101,
    category: 'animal welfare',
    title: 'Cat Adoption day',
    description: 'Find your new feline friend and this event.',
    location: 'Meow Town',
    date: 'January 28, 2022',
    time: '12:00',
    petsAllowed: true,
    organizer: 'Kat Laydee',
  },
  {
    id: 4582797,
    category: 'food',
    title: 'Community Gardening',
    description: 'Join us as we tend to the community edible plants',
    location: 'Clora City',
    date: 'March 14, 2022',
    time: '10:00',
    petsAllowed: true,
    organizer: 'Fern Pollin',
  },
  {
    id: 9419988,
    category: 'susstainability',
    title: 'Beach Cleanup',
    description: 'Help pick up trash along the shore.',
    location: 'Playa Del Carmen',
    date: 'July 22, 2022',
    time: '11:00',
    petsAllowed: true,
    organizer: 'Corey Wales',
  },
  
])
*/
onMounted(()=>{
  // console.log(this.$refs.test)
  EventServices.getEvents()
  .then((response)=>{
    console.log('events: ', response.data)
    events.value =  response.data
  })
  .catch((error)=>{
    console.log(error)
  })
})

/**/
</script>

<template>
  
  <div class="home">
    <h1>Events For Good</h1>
    <div class="events">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
      <!-- <EventCard /> -->
    </div>
  </div>

</template>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>