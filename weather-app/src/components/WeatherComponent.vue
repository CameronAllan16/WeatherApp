import axios from "axios";

export default { 
    data() 
    { return 
        { api_key:
"27bcc252742830381afd6856832da01a", url_base:
"https://api.openweathermap.org/data/2.5/", weather_icon:
"http://openweathermap.org/img/wn/", 
query: "", 
weather: {}, }; },
};

<template>
    
  <div class="weather-container">
    <div class="weather-wrap">
      <div class="search-box">
        <input
          type="text"
          placeholder="Search..."
          class="search-bar"
          v-model="query"
          v-on:keypress="fetchWeather"
        />
      </div>
      <div class="weather-info" v-if="typeof weather.main != undefined'">
        <div class="location-box">
          <div class="location">
            {{ weather.name }},{{ weather.sys.country }}
          </div>
          <div class="date">{{ todaysDate() }}</div>
        </div>
        <div class="weather-box">
          <div class="temp">{{ Math.round(weather.main.temp) }}°c</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
          <div class="icon">
            <img:src
              ="`${weather_icon}${weather.weather[0].icon}${'@2x.png'}`"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
