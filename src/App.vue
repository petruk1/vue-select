<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div class="selection-container">
      <MatSelect :options="fruits"
                 :placeholder="placeholder"
                 :label="label"
                 @change="logUserPick($event)"
                 v-model="fruitId"></MatSelect>
      <div>User choose: {{userDidSelect.name}}</div>
    </div>
  </div>
</template>

<script>
import MatSelect from './components/MatSelect.vue';

export default {
  name: 'app',
  components: {
    MatSelect,
  },
  computed: {
    userDidSelect() {
      return this.fruits.find(x => x.id === this.fruitId);
    },
  },
  methods: {
    logUserPick(e) {
      console.log(e);
    },
  },
  data() {
    return {
      fruitId: 1,
      placeholder: 'Choose something',
      label: 'Fruit',
      fruits: [{
        id: 1,
        name: 'Pineapple',
      }, {
        id: 2,
        name: 'Chery',
      }, {
        id: 3,
        name: 'Orange',
      }],
    };
  },
};
</script>

<style>
  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .selection-container {
    display: flex;
    align-items: center;
  }

  .selection-container *:first-child {
    margin-right: 20px;
  }
</style>
