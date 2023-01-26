<template>
  <div id="app">
    <Life></Life>
  </div>
</template>

<script>
import Life from './components/Life.vue'

export default {
  name: 'App',
  components: {
    Life
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #9c27b0;
  margin-top: 60px;
}
</style>
