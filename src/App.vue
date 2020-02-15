<template>
  <div id="app">
    <h1>My Favorite Mechanical Switches</h1>
    <switch-list />
  </div>
</template>

<script>
import SwitchList from './components/SwitchList.vue'

export default {
  name: 'App',
  components: {
    SwitchList
  }
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
