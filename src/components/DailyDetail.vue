<template>
    <div class="daily-detail">
        <div class="u-display-flex u-margin-top-small u-flex-between">
            <button>daily summary</button>
            <button>hourly</button>
        </div>
        <PlanetChart />
    </div>
</template>

<script>
import PlanetChart from './PlanetChart.vue'

export default {
    components: {
        PlanetChart
    }
}
</script>

<style scoped>
.daily-detail {
    margin-left: 1rem;
    margin-right: 1rem;
}
</style>