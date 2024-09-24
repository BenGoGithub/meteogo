<template>
  <div class="cities-list">
    <h1>Liste des villes</h1>
    <div v-for="city in cities" :key="city.id">
      <CityWeather
          :name="city.name"
          :weather="city.weather"
          :temperature="city.temperature"
          :updatedAt="city.updatedAt"
      />
    </div>
  </div>
</template>

<script>
import CityWeather from './City.vue'

export default {
  name: 'CitiesList',
  components: {
    CityWeather
  },
  props: {
    msg: String
  },
  data() {
    return {
      cities: [
        {
          id: 1,
          name: 'Ville 1',
          weather: 'Ensoleillé',
          temperature: 22.0,
          updatedAt: new Date()
        },
        {
          id: 2,
          name: 'Ville 2',
          weather: 'Peu nuageux',
          temperature: 19.5,
          updatedAt: new Date()
        }
      ]
    }
  }
}
</script>

<style scoped>
h1 {
  text-align: center;
  color: #FF885B; /* Une couleur verte agréable */
}

.city-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.city-list > div {
  width: 100%; /* Prendre toute la largeur */
  max-width: 400px; /* Limiter la largeur maximale */
}
</style>