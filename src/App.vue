<template>
  <div id="app">
    <h1>Sally's Favorite Mechanical Switches</h1>
    <switch-form
      @add:switch="addSwitch"
    />
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
          name: 'Alpaca',
          type: 'Linear',
          bottomOutForce: '62g',
        },
        {
          id: uuidv4(),
          name: 'Silent Alpaca',
          type: 'Linear',
          bottomOutForce: '62g',
        },
        {
          id: uuidv4(),
          name: 'Gateron Clear',
          type: 'Linear',
          bottomOutForce: '45g',
        },
        {
          id: uuidv4(),
          name: 'Gateron Yellow',
          type: 'Linear',
          bottomOutForce: '60g',
        },
        {
          id: uuidv4(),
          name: 'Kailh BOX White',
          type: 'Clicky',
          bottomOutForce: '60g',
        },
        {
          id: uuidv4(),
          name: 'Kailh BOX Pink',
          type: 'Clicky',
          bottomOutForce: '55g',
        },
        {
          id: uuidv4(),
          name: 'Kailh Choc White',
          type: 'Clicky',
          bottomOutForce: '50g',
        },
      ]
    }
  },
  methods: {
    addSwitch(switchToAdd) {
      const newSwitch = {
        ...switchToAdd,
        id: uuidv4(),
      }
      this.switches.push(newSwitch);
    },
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

#app td {
  text-overflow: clip;
}

#app input[type='text'] {
  width: 100%;
}
</style>