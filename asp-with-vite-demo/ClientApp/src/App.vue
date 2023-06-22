<script setup lang="ts">
import { ref } from 'vue';

const weatherData = ref();
const getData = async () => {
  const resp =  await fetch(`${import.meta.env.BASE_URL}api/WeatherForecast`);
  weatherData.value = await resp.json();
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  </header>

  <main>
    <button @click="getData()">Get weather</button>
    <p v-if="weatherData">{{ weatherData }}</p>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
