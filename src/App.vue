<template>
  <ThemeSelector></ThemeSelector>
  <BackToHome v-if="appIndex != 'Home'" @click="appIndex = 'Home'"></BackToHome>
  <div v-if="appIndex === 'Home'" class="home">
    <h1>Apps</h1>
    <div class="pageOptions">
      <button @click="changePage('trafficLight')">Traffic Light Simulator</button>
      <button @click="changePage('numCounter')">Counter of Numbers</button>
      <button @click="changePage('trafficLight')">Traffic Light Simulator</button>
    </div>
  </div>
  <NumCounter v-if="appIndex === 'numCounter'"></NumCounter>
</template>

<script>
import ThemeSelector from './components/ThemeSelector.vue'
import BackToHome from './components/BackToHome.vue'
import NumCounter from './components/NumCounter.vue'

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
    NumCounter
  },
  methods: {
    changePage(index) {
      this.appIndex = index
      switch (index) {
        case 'trafficLight':
          break
        case 'numCounter':
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
