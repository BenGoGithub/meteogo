<script>
export default {
  props: {
    msg: String
  },
  data() {
    return {
      name: 'Ma ville',
      weather: 'Peu nuageux',
      temperature: 20.55,
      updatedAt: new Date()
    }
  }
}
</script>

<template>
  <div class="weather-card">
    <h1>{{ msg }}</h1>
    <h2>{{ name }}</h2>
    <p>Météo: {{ weather }}</p>
    <p>Température: {{ temperature.toFixed(1) }}°C</p>
    <p>Mise à jour: {{ updatedAt.toLocaleString() }}</p>
  </div>
</template>

<style scoped>
.weather-card {
  background-color: #f0f0f0;
  border-radius: 8px;
  padding: 20px;
  margin-top: 20px;
}
</style>