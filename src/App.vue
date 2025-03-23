<script setup>
import { ref } from 'vue'
import SearchInput from './components/SearchInput.vue';
import WeatherCard from './components/WeatherCard.vue';
const places = ref([])

const addPlace = (data) => {
  places.value.push(data)
}

</script>
<template>
  
  <main>
    <!-- Date -->
     <div class="text-center mb-6">
      {{ new Date().toLocaleDateString('len-us',{
        weekday: 'long',
        year: 'numeric',
        month:'long',
        day:'numeric'
      }) }}
     </div>

    <!-- Search -->
     <SearchInput @place-data="addPlace"/>
    
    <!-- Weather Cards -->
     <div v-for="(place, idx) in places" :key="idx">
      <WeatherCard :place="place"/>
     </div>
  </main>
</template>