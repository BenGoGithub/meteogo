<script setup>
import HelloWorld from './components/CitiesList.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/Renardmeteo.png" width="524" height="524" />
    <HelloWorld msg="Météo Vue" />
  </header>
</template>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.image-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  margin-bottom: 20px; /* Ajoute un espace entre l'image et le contenu suivant */
}

.logo {
  max-width: 100%;
  height: auto;
  border-radius: 15px;
}
</style>