<template>
    <div class="container">
        <div class="col-1 temperature">
            <div class="title">{{ temperatureValue }}</div>
            <div class="unit">
                <span class="active-unit">°C</span>
                <hr style="width: 4rem; margin-top: 0; margin-bottom: 0; margin-left: 0; margin-right: 0">
                <span class="secondary-unit">°F</span>
            </div>
        </div>
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
    </div>

</template>

<script>
export default {
    props: {
        temperatureValue: Number,
        temperatureUnit: String,
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
.title {
    font-size: 10rem;
}

.unit {
    display: flex;
    flex-direction: column;
    padding-top: 1.4rem;
    align-items: flex-end;
}

.active-unit {
    font-size: 4.2rem;
}

.secondary-unit {
    font-size: 2rem;
}

.temperature {
    display: flex;
}

.weather-info {
    font-size: 2.4rem;
    line-height: 1.2;
    align-self: baseline;
    text-align: left;
}

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

.weather-info-detail-item {
    padding: 5px;
}
</style>