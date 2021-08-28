<template>
    <div class="col-1 weather-info">
        <div>{{ currentStatus }}</div>

        <ul class="weather-info-detail">
            <li class="weather-info-detail-item">Feels Like {{ feelLike }}°</li>
            <li class="weather-info-detail-item">Wind {{ wind }} km/h</li>
            <li class="weather-info-detail-item">Barometer {{ barometer }}°</li>
            <li class="weather-info-detail-item">Visibility {{ visibility }} km</li>
            <li class="weather-info-detail-item">Humidity {{ humidity }}%</li>
            <li class="weather-info-detail-item">Dew Point {{ dewPoint }}°</li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        currentStatus: String,
        feelLike: Number,
        barometer: Number,
        humidity: Number,
        wind: Number,
        visibility:  Number,
        dewPoint: Number
    }
}
</script>

<style scoped>
ul {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    height: 7rem;
}

.weather-info-detail {
    list-style: none;
    text-align: left;
    padding-left: 0;
    font-size: 1.3rem;
}
</style>