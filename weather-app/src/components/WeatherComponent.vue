<script>
import axios from 'axios';
export default {
    data() {
        return {
            api_key: `${process.env.WEATHER_API_KEY}`,
            url_base: "https://api.openweathermap.org/data/2.5/",
            weather_icon: "http://openweathermap.org/img/wn/",
            query: "",
            weather: {},
        };
    },
    methods: {
        async fetchWeather(e) {
            
            if (e.key == "Enter") { let response = await axios.get(`${this.url_base}weather? q=${this.query}&units=metric&APPID=${this.api_key}`); this.setResults(response.data); }
        }, setResults(returnedResponse) {
            this.weather = returnedResponse;
        },
        todaysDate() {
            return new Date().toDateString();
        }
    }

};


</script>
<template>
    <div class="weather-container">
        <div class="weather-wrap">
            <div class="search-box">
                <input type="text" placeholder="Search..." class="search-bar" v-model="query"
                    v-on:keypress="fetchWeather" />
            </div>
            <div class="weather-info">
                <div class="location-box">
                    <div class="location">

                    </div>
                    <div class="date">{{ todaysDate() }}</div>
                </div>
                <div class="weather-box">
                    <div class="temp">°f</div>
                    <div class="weather"></div>
                    <div class="icon">
                        <!-- <img :src="`${weather_icon}${weather.weather[0].icon}${'@2x.png'}`" /> -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
