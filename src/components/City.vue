<template>
  <div class="weather-card">
    <h2>{{ name }}</h2>
    <p>Météo: {{ weather }}</p>
    <p>Température: {{ temperature.toFixed(1) }}°C</p>
    <p>Mise à jour: {{ formattedDate }}</p>
  </div>
</template>

<script>
import { format } from 'timeago.js'

export default {
  name: 'CityWeather',
  props: {
    name: String,
    weather: String,
    temperature: Number,
    updatedAt: Date
  }, computed: {
    formattedDate() {
      return format(this.updatedAt, 'fr');
    }
  }
}
</script>

<style scoped>
.weather-card {
  background-color: #f0f0f0;
  border-radius: 8px;
  padding: 20px;
  margin-top: 20px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;
}

.weather-card:hover {
  transform: scale(1.02);
}

h2 {
  color: #333;
}

p {
  font-size: 16px;
  color: #555;
}
</style>