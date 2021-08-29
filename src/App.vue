<template>
  <div class="home-screen">
    <TodayWeather 
      :temperatureValue="temperatureValue"
      :temperatureUnit="'C'"
      :currentStatus="currentStatus"
      :feelLike="feelLike"
      :wind="wind"
      :barometer="barometer"
      :visibility="visibility"
      :humidity="humidity"
      :dewPoint="dewPoint"
      :weatherData="weatherData" />
    
    <WeatherList :weatherList="weatherList" @clicked="getWeatherDataRenderingChart"/>

    <DailyDetail />
  </div>
</template>

<script>
import TodayWeather from './components/TodayWeather.vue'
import WeatherList from './components/WeatherList.vue'
import DailyDetail from './components/DailyDetail.vue'
import { format } from 'date-fns'

const ApiKey = '6028a1a7dea7eb6ac78b16fb95bc5c29'

export default {
  name: 'App',
  components: {
    TodayWeather,
    WeatherList,
    DailyDetail
  },
  data() {
    return {
      weatherData: Object,
      temperatureValue: Number,
      visibility: Number,
      feelLike: Number,
      humidity: Number,
      wind: Number,
      currentStatus: String,
      barometer: Number,
      dewPoint: Number,
      weatherList: Object,
      originalWeatherList: Array
    }
  },
  methods: {
    groupByDate(list = []) {
      if (!list.length) {
        return list
      }

      return list.reduce((pre, curr) => {
        if (!pre.length) {
          let date = curr.dt_txt.split(' ')[0].toString()
          return {
            ...pre,
            [date]: {
              ...curr,
              displayDate: format(new Date(date), 'E dd')
            }
          }
        }
      }, {})
    },
    fetchWeather() {
      const url = `http://api.openweathermap.org/data/2.5/forecast?q=ho chi minh&appid=${ApiKey}&units=metric`;
      fetch(url)
        .then(response => response.json())
        .then(data => {
          this.currentStatus = data.list[0].weather[0].main;
          this.temperatureValue = Math.floor(data.list[0].main.temp);
          this.barometer = data.list[0].main.temp.pressure;
          this.visibility = data.list[0].visibility;
          this.feelLike = data.list[0].main.feels_like;
          this.humidity = data.list[0].main.humidity;
          this.wind = data.list[0].wind.speed;
          this.dewPoint = 0;

          this.originalWeatherList = data.list;
          this.weatherList = this.groupByDate(data.list);
        })
    },
    getWeatherDataRenderingChart(value) {
      console.log(value);
    }
  },
  created() {
    this.fetchWeather()
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

.u-flex-align-items-center {
  align-items: center;
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
