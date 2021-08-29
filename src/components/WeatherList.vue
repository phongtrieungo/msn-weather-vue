<template>
  <div class="weather-list">
    <ul class="scroll-menu">
      <li v-for="(value, name) in weatherList" :key="name" v-on:click="onSelectWeather(name)">
          <div class="u-flex-column">
            <span>{{ value.displayDate }}</span>
            <span class="u-display-flex u-flex-align-items-center">
              <img v-bind:src="`http://openweathermap.org/img/wn/${value.weather[0].icon}@2x.png`" class="weather-status-icon">
              {{ value.weather[0].main }}
            </span>
            <span>{{ value.main.temp_max }} °C</span>
            <span>{{ value.main.temp_min }} °C</span>
          </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    weatherList: Object
  },
  methods: {
    onSelectWeather(selected) {
      this.$emit('clicked', selected);
    }
  }
};
</script>

<style scoped>
.weather-list {
  display: flex;
}

.scroll-menu {
    list-style: none;
    overflow: auto;
    white-space: nowrap;
    margin: 0;
    padding-left: 0;
    margin-left: 1rem;
    margin-right: 1rem;
}

li {
    padding: 1.5rem;
    display: inline-block;
    text-decoration: none;
}

li:hover {
    cursor: pointer;
    background-color: rgba(255,255,255,.1);
    border: 1px solid white;
    border-bottom: none;
}

li:not(:hover) {
    border-bottom: 1px solid white;
}

.weather-status-icon {
  width: 3rem;
  height: 3rem;
}

@media only screen and (min-width: 768px) {
    li {
        padding: 1rem;
        border-radius: 5px;
        background-color: azure;
        margin: 5px;
    }
}

</style>