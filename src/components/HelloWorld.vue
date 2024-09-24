<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <CityWeather
        :name="cityData.name"
        :weather="cityData.weather"
        :temperature="cityData.temperature"
        :updatedAt="cityData.updatedAt"
    />
  </div>
</template>

<script>
import CityWeather from './City.vue'

export default {
  name: 'HelloWorld',
  components: {
    CityWeather
  },
  props: {
    msg: String
  },
  data() {
    return {
      cityData: {
        name: 'Ma ville',
        weather: 'Peu nuageux',
        temperature: 20.55,
        updatedAt: new Date()
      }
    }
  }
}
</script>