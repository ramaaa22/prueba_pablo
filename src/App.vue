<template>
  <div id="app">
    <ejer-pablo/>
  </div>
</template>

<script>
import EjerPablo from './components/EjerPablo.vue'


export default {
  name: 'app',
  components: {
    EjerPablo
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
