<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <BaseCard msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import BaseCard from './components/BaseCard.vue'

export default {
  name: 'App',
  components: {
    BaseCard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
