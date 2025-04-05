<template>
    <div class="traffic-box">
        <div class="traffic-container">
        <div class="light-box">
                <div class="light-circle">
                    <div class="circle" id="red" :class="{ active: color === 0 }"></div>
                    <div class="circle" id="yellow" :class="{ active: color === 1 }"></div>
                    <div class="circle" id="green" :class="{ active: color === 2 }"></div>
                </div>
            </div>
            <div class="counter-box">
                <h3>
                    {{ trafficTimer[color] }}
                </h3>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "TrafficLight",
  data() {
    return {
      trafficTimerPresets: [10, 3, 5], // vermelho, amarelo, verde
      trafficTimer: [10, 3, 5],
      color: 0,
      intervalId: null,
    };
  },
  mounted() {
    this.intervalId = setInterval(() => {
      if (this.trafficTimer[this.color] > 0) {
        this.trafficTimer[this.color]--;
      }

      if (this.trafficTimer[this.color] === 0) {
        this.color = (this.color + 1) % 3;
        this.trafficTimer = [...this.trafficTimerPresets];
      }
    }, 1000);
  },
  beforeUnmount() {
    clearInterval(this.intervalId);
  },
};
</script>

<style scoped>
  @font-face {
  font-family: 'DS-Digital';
  src: url('../assets/DS-DIGIB.TTF') format('truetype');
  font-weight: normal;
  font-style: normal;
  }


  .traffic-box{
      width: 20em;
      display: flex;
      margin: auto;
      background-color: aliceblue;
  }

  .traffic-container {
      background-color: rgb(38, 41, 41);
      width: 20em;
      margin: auto;
      display: flex;
      justify-content: space-around;
      align-items: center;
      padding: 10px;
      padding-block: 15px;
      max-width: 100%;
      box-sizing: border-box;
  }

  .light-box {
      display: flex;
      justify-content: center;
      width: 10em;
      height: 20em;
      justify-items: center;

      width: 45%;
  }

  .light-circle {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      width: 10em;
      height: 100%;
      background-color: rgb(70, 70, 70);
      border: 2px solid black;
      border-radius: 5px;
  }

  .circle {
      margin-block: 5px;
      border-radius: 50%;
      height: 5.5em;
      width: 5.5em;
      background-color: rgb(46, 46, 46);
  }

  #red.active {  background-color: red; opacity: 1;  }
  #yellow.active {  background-color: yellow; opacity: 1;  }
  #green.active {  background-color: green; opacity: 1;  }

  .counter-box {
      width: 45%;
      height: 20em;
      display: flex;
      justify-content: center;
      align-items: center;
  }

  .counter-box h3 {
      font-size: 50pt;
      color: white;
      font-family: 'DS-Digital';
  }
</style>