<template>
  <div class="home-screen">
    <TodayWeather 
      temperatureValue=27
      temperatureUnit="C"
      currentStatus="Light rain"
      feelLike=26
      wind=2
      barometer=1007.00
      visibility=8
      humidity=100
      dewPoint=26 />
    
    <WeatherList />

    <DailyDetail />
  </div>
</template>

<script>
import TodayWeather from './components/TodayWeather.vue'
import WeatherList from './components/WeatherList.vue'
import DailyDetail from './components/DailyDetail.vue'

export default {
  name: 'App',
  components: {
    TodayWeather,
    WeatherList,
    DailyDetail
  }
}
</script>

<style>
body {
  background-image: url('./assets/rain-bg.jpg');
  background-color: #cccccc;
  background-position: center; /* Center the image */
  background-repeat: no-repeat; /* Do not repeat the image */
  background-size: auto;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f9f9fa;
  margin-top: 60px;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  
}

button {
  text-transform: uppercase;
  border: none;
  padding: 1rem;
  font-weight: bolder;
  background-color: rgba(255,255,255,.1);
  color: #f9f9fa;
}

button:hover {
  cursor: pointer;
  background-color: rgba(255,255,255,.5);
}

.container {
    margin: 2rem;
}

.u-flex-column {
    display: flex;
    flex-direction: column;
}

.u-display-flex {
  display: flex;
}

.u-flex-between {
  justify-content: space-between;
}

.u-margin-top-small {
  margin-top: 1rem;
}

[class*="col-"] {
  width: 100%;
}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {
  .container {
    display: flex;
  }
  .col-1 {
    width: 50%;
  }
}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {}

/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {}

</style>
