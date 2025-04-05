<template>
  <h1>{{ appIndex }}</h1>
  <ThemeSelector></ThemeSelector>
  <BackToHome v-if="appIndex != 'Home'" @click="appIndex = 'Home'"></BackToHome>
  <div v-if="appIndex === 'Home'" class="home">
    <div class="pageOptions">
      <button @click="changePage('Traffic Light Simulator')">Traffic Light Simulator</button>
      <button @click="changePage('Counter of Numbers')">Counter of Numbers</button>
      <button @click="changePage('Traffic Light Simulator')">Traffic Light Simulator</button>
    </div>
  </div>
  <NumCounter v-if="appIndex === 'Counter of Numbers'"></NumCounter>
  <TrafficLight v-if="appIndex === 'Traffic Light Simulator'"></TrafficLight>
</template>

<script>
import ThemeSelector from './components/ThemeSelector.vue'
import BackToHome from './components/BackToHome.vue'
import NumCounter from './components/NumCounter.vue'
import TrafficLight from './components/TrafficLight.vue'

export default {
  name: 'App',
  data() {
    return {
      appIndex: 'Home'
    }
  }, 
  components: {
    ThemeSelector,
    BackToHome,
    NumCounter,
    TrafficLight
  },
  methods: {
    changePage(index) {
      this.appIndex = index
      switch (index) {
        case 'Traffic Light Simulator':
          break
        case 'Counter of Numbers':
          break
      }
    }
  }
}
</script>

<style>
.pageOptions {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 5em;
}

button {
  height: 70px;
  width: 23em;
  background-color: darkslateblue;
  border: none;
  border-radius: 5px;
  transition: background-color 0.2s ease, border 0.2s ease, color 0.2s ease;
  color: white;
  margin: 0 0 15px 0;
}

button:hover {
  background-color: v-bind(bgColor);
  border: 1px solid darkslateblue;
  color: darkslateblue;
}

h1 {
  color: v-bind(textColor);
  font-size: 40px;
  margin-top: 2em;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: darkslateblue;
}
</style>
