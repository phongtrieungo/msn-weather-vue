<template>
  <div class="chart">
    <canvas id="planet-chart"></canvas>
  </div>
</template>

<script>
import Chart from 'chart.js'
import planetChartData from './planet-data'

export default {
  name: 'PlanetChart',
  data() {
    return {
      planetChartData
    }
  },
  mounted() {
    const ctx = document.getElementById('planet-chart');
    new Chart(ctx, this.planetChartData);
  }
}
</script>

<style scoped>
.chart {
  background-color: bisque;
  margin-top: 1rem;
}
</style>