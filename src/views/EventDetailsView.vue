
<script setup>
    import { ref, onMounted } from 'vue';
    import EventServices from '@/services/EventServices';

    const event = ref(null)
    // const id = ref(123)
    const props = defineProps({
        id: {
            required: true,
        },
    })

    onMounted(() => {
        EventServices.getEvent(props.id)
        .then((response)=>{
            console.log('events: ', response.data)
            event.value =  response.data
        })
        .catch((error)=>{
            console.log(error)
        })
    })
</script>

<template>
    <div  v-if="event">
       <h1>{{ event.title }}</h1> 
       <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
       <p>{{ event.description }}</p>
    </div>
</template>

<style scoped>
    
</style>
