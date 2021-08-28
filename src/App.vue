<template>
  <TodayWeather 
    temperatureValue="27"
    temperatureUnit="C"
    currentStatus="Light rain"
    feelLike="26"
    wind="2"
    barometer="1007.00"
    visibility="8"
    humidity="100"
    dewPoint="26" />
</template>

<script>
import TodayWeather from './components/TodayWeather.vue'

export default {
  name: 'App',
  components: {
    TodayWeather
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
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
