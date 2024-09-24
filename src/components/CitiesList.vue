<template>
  <div class="cities-list">
    <h1>Liste des villes</h1>
    <div v-if="loading">Chargement en cours...</div>
    <div v-if="error" style="color: red;">{{ error }}</div>
    <div class="cities-grid">
      <div v-for="city in cities" :key="city.id" class="city-item">
        <CityWeather
            :name="city.name"
            :weather="city.weather"
            :temperature="city.temperature"
            :updatedAt="city.updatedAt"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CityWeather from './City.vue'
import axios from 'axios';
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
      cities: [],
      loading: false,
      error: null
    }
  },
        created() {
      this.fetchWeatherData()
    },
    methods: {
      fetchWeatherData() {
        this.loading = true;
        this.error = null;
        axios.get('https://api.openweathermap.org/data/2.5/find?lat=45.188&lon=5.724&cnt=20&cluster=yes&lang=fr&units=metric&APPID=bf8694d48e78df7a7f93becf20d054c9')
            .then(response => {
              this.cities = response.data.list.map(city => ({
                id: city.id,
                name: city.name,
                weather: city.weather[0].description,
                temperature: city.main.temp,
                updatedAt: new Date(city.dt * 1000)
              }));
            })
            .catch(error => {
              this.error = "Erreur lors de la récupération des données météo";
              console.error(error);
            })
            .finally(() => {
              this.loading = false;
            });
      }
    }
}
</script>
<style scoped>
h1 {
  text-align: center;
  color: #FF885B;
}

.cities-list {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}

.cities-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

.city-item {
  width: 100%;
}

@media (max-width: 1200px) {
  .cities-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 900px) {
  .cities-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .cities-grid {
    grid-template-columns: 1fr;
  }
}
</style>