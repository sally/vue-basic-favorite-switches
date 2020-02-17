<template>
  <div id="app">
    <h1>Sally's Favorite Mechanical Switches</h1>
    <switch-form />
    <switch-list :switches="switches"
      @update:switch="updateSwitch"
      @delete:switch="deleteSwitch"
    />
  </div>
</template>

<script>
import SwitchForm from './components/SwitchForm.vue';
import SwitchList from './components/SwitchList.vue';

const uuidv4 = require('uuid/v4');

export default {
  name: 'App',
  components: {
    SwitchForm,
    SwitchList,
  },
  data() {
    return {
      switches: [
        {
          id: uuidv4(),
          brand: 'Alpaca',
          name: 'Alpaca',
          type: 'Linear',
          bottomOutForce: '62g',
        },
        {
          id: uuidv4(),
          brand: 'Alpaca',
          name: 'Silent Alpaca',
          type: 'Linear',
          bottomOutForce: '62g',
        },
        {
          id: uuidv4(),
          brand: 'Gateron',
          name: 'Clear',
          type: 'Linear',
          bottomOutForce: '45g',
        },
        {
          id: uuidv4(),
          brand: 'Gateron',
          name: 'Yellow',
          type: 'Linear',
          bottomOutForce: '60g',
        },
        {
          id: uuidv4(),
          brand: 'Kailh',
          name: 'BOX White',
          type: 'Clicky',
          bottomOutForce: '60g',
        },
        {
          id: uuidv4(),
          brand: 'Kailh',
          name: 'BOX Pink',
          type: 'Clicky',
          bottomOutForce: '55g',
        },
        {
          id: uuidv4(),
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
  methods: {
    updateSwitch(switchToUpdate) {
      this.switch = this.switches.map(mechSwitch => {
        mechSwitch.id === switchToUpdate.id ? switchToUpdate : mechSwitch;
      })
    },
    deleteSwitch(idToDelete) {
      this.switches = this.switches.filter(mechSwitch => mechSwitch.id != idToDelete);
    }
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
