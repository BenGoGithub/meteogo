<template>
  <div class="weather-card">
    <h2>{{ name }}</h2>
    <p>Météo: {{ weather }}</p>
    <p>Température: {{ temperature.toFixed(1) }}°C</p>
    <p>Mise à jour: {{ updatedAt.toLocaleString() }}</p>
  </div>
</template>

<script>
export default {
  name: 'CityWeather',
  props: {
    name: String,
    weather: String,
    temperature: Number,
    updatedAt: Date
  }
}
</script>

<style scoped>
.weather-card {
  background-color: #f0f0f0;
  border-radius: 8px;
  padding: 20px;
  margin-top: 20px;
}
</style>