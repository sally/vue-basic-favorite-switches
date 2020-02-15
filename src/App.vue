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
  },
  data() {
    return {
      switches: [
        {
          id: 1,
          brand: 'Alpaca',
          name: 'Alpaca',
          type: 'Linear',
          bottomOutForce: '62g',
        },
        {
          id: 2,
          brand: 'Alpaca',
          name: 'Silent Alpaca',
          type: 'Linear',
          bottomOutForce: '62g',
        },
        {
          id: 3,
          brand: 'Gateron',
          name: 'Clear',
          type: 'Linear',
          bottomOutForce: '45g',
        },
        {
          id: 4,
          brand: 'Gateron',
          name: 'Yellow',
          type: 'Linear',
          bottomOutForce: '60g',
        },
        {
          id: 5,
          brand: 'Kailh',
          name: 'BOX White',
          type: 'Clicky',
          bottomOutForce: '60g',
        },
        {
          id: 6,
          brand: 'Kailh',
          name: 'BOX Pink',
          type: 'Clicky',
          bottomOutForce: '55g',
        },
        {
          id: 7,
          brand: 'Kailh',
          name: 'Choc White',
          type: 'Clicky',
          travelDistance: '3mm',
          actuationForce: '50g',
          bottomOutForce: '50g',
        },
      ]
    }
  },
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
