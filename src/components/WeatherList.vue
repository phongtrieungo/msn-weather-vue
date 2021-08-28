<template>
  <div class="weather-list">
    <ul class="scroll-menu">
      <li v-for="weather in weatherList" :key="weather.date">
          <div class="u-flex-column">
            <span>{{ weather.date }}</span>
            <span>{{ weather.status }}</span>
            <span>{{ weather.high }}</span>
            <span>{{ weather.low }}</span>
          </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { format, addDays } from 'date-fns'

const weatherList = [
  {
    date: format(addDays(new Date(), 0), 'E dd'),
    high: 32,
    low: 25,
    humidity: 68,
    status: "thunder",
  },
  {
    date: format(addDays(new Date(), 1), 'E dd'),
    high: 32,
    low: 25,
    humidity: 66,
    status: "thunder",
  },
  {
    date: format(addDays(new Date(), 2), 'E dd'),
    high: 32,
    low: 25,
    humidity: 75,
    status: "thunder",
  },
  {
    date: format(addDays(new Date(), 3), 'E dd'),
    high: 32,
    low: 25,
    humidity: 75,
    status: "thunder",
  },
  {
    date: format(addDays(new Date(), 4), 'E dd'),
    high: 32,
    low: 25,
    humidity: 75,
    status: "thunder",
  },
  {
    date: format(addDays(new Date(), 5), 'E dd'),
    high: 32,
    low: 25,
    humidity: 75,
    status: "thunder",
  },
];
export default {
  data: () => ({
      weatherList
  })
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

@media only screen and (min-width: 768px) {
    li {
        padding: 1rem;
        border-radius: 5px;
        background-color: azure;
        margin: 5px;
    }
}

</style>