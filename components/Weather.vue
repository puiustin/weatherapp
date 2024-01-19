<template>
  <div style="margin-top: 2rem">
    <div class="header container">
      <h1>WeatherApp</h1>
      <div
        style="
          display: flex;
          justify-content: center;
          height: 60px;
          margin-top: 1rem;
        "
      >
        <div class="search-container">
          <div
            class="searchbar"
            style="display: flex; justify-content: center"
          ></div>
        </div>

        <input type="text" placeholder="Enter a location" />
      </div>
      <button @click="toggleComponent" class="btn-search">Search</button>
    </div>
  </div>
  <div class="wrapper">
    <div class="widget-container">
      <div class="top-left">
        <h1 id="name">
          {{ weather.location.name }} , {{ weather.location.country }}
        </h1>
        <h2 id="day" v-if="weather.current.is_day === 1">Day</h2>
        <h2 id="night" v-else-if="weather.current.is_day === 0">Night</h2>
        <h3 id="lastupdate">Last update: {{ weather.current.last_updated }}</h3>
        <p class="geo"></p>
      </div>
      <div class="top-right">
        <h1 id="weather-status">Weather / Weather Status</h1>
        <h2 id="weather-status" style="font-weight: 600">
          {{ weather.current.condition.text }}
        </h2>

        <img
          class="weather-icon"
          src="//cdn.weatherapi.com/weather/64x64/day/116.png"
        />
        <!-- src="https://myleschuahiock.files.wordpress.com/2016/02/sunny2.png" -->
      </div>
      <div class="horizontal-half-divider"></div>
      <div class="bottom-left">
        <h1 id="temperature">{{ weather.current.temp_c }}</h1>
        <h2 id="celsius">&degC</h2>
        <h3 id="feelslike">
          Feels like {{ weather.current.feelslike_c }} &degC
        </h3>
      </div>
      <div class="vertical-half-divider"></div>
      <div class="bottom-right">
        <div class="other-details-key">
          <p>Wind Speed</p>
          <p>Humidity</p>
          <p>Pressure</p>
        </div>
        <div class="other-details-values">
          <p class="windspeed">{{ weather.current.wind_kph }} Km/h</p>
          <p class="humidity">{{ weather.current.humidity }} %</p>
          <p class="pressure">{{ weather.current.pressure_mb }} mb</p>
        </div>
      </div>
    </div>
  </div>

  <div class="wrapper">
    <div class="widget-container">
      <div class="top-left">
        <h1 id="name">Forecast</h1>
        <p class="geo"></p>
      </div>
      <div class="top-right">
        <h1 id="weather-status">Weather / Weather Status</h1>
        <img
          class="weather-icon"
          src="//cdn.weatherapi.com/weather/64x64/day/116.png"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["userInput"]);
let aux =
  "http://api.weatherapi.com/v1/current.json?key=3c447b55b60e470e9a992423241301&q=" +
  props;

const { data: weather } = await useFetch(
  "http://api.weatherapi.com/v1/current.json?key=3c447b55b60e470e9a992423241301&q=Barcelona"
);
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700,900&display=swap");

:root {
  --gradient: linear-gradient(135deg, #72edf2 10%, #5151e5 100%);
}

* {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  line-height: 1.25em;
}

/* .clear {
  clear: both;
} */

/* body {
  width: 100%;
  height: 100%;
  background-color: #252525;
  margin: 0;
  padding: 0;
  font-family: "Montserrat", sans-serif;
  color: #fff;
} */

.widget-container {
  width: 80%;
  height: 412px;
  display: block;
  background-color: #252525;
  border-radius: 25px;
  margin: 0 auto;
  margin-top: 1rem;
  color: #fff;
}

/* Widget 4 Quarter Division here */

.top-left {
  height: 60%;
  width: 50%;
  /*   background-color:red; */
  padding: 55px 0 0 70px;
  display: inline-block;
}

.top-right {
  height: 60%;
  width: 50%;
  /*   background-color: blue; */
  float: right;
  padding: 55px 0 0 0;
}

.bottom-left {
  height: 40%;
  width: 45%;
  /*   background-color:orange; */
  float: left;
  margin: 0;
  padding: 40px 0 0 50px;
}

.bottom-right {
  height: 40%;
  width: 55%;
  /*   background-color: brown; */
  float: right;
  padding: 25px 0 0 60px;
}

h1,
h2,
h3,
p {
  margin: 0;
  padding: 0;
}

/* Top-left Div CSS */

#city {
  font-weight: 900;
  font-size: 25px;
}

#day {
  font-weight: 700;
  font-size: 25px;
  margin-top: 18px;
}

#date {
  font-weight: 500;
  font-size: 20px;
  margin-top: 4px;
}

#time {
  font-weight: 400;
  font-size: 18px;
  margin-top: 8px;
}

#codepen-link {
  font-weight: 400;
  font-size: 12px;
  margin-top: 20px;
}

.top-left > a {
  text-decoration: none;
  color: white;
}

.top-left > a:hover {
  color: #b0bec5;
}

/* Top-Right Div CSS */

#weather-status {
  font-size: 18px;
  font-weight: 300;
  text-align: center;
  margin: 0 auto;
}

.top-right > img {
  width: 120px;
  height: 120px;
  display: block;
  margin: 15px auto 0 auto;
}

/* Horizontal-Half-divider */

.horizontal-half-divider {
  width: 100%;
  height: 3px;
  margin-top: -5px;
  background-color: #ababab;
}

.vertical-half-divider {
  width: 3px;
  position: absolute;
  height: 167px;
  background-color: #ababab;
  display: inline-block;
  padding: 0;
}

/* Bottom-left CSS */

#temperature,
#celsius,
#temp-divider,
#fahrenheit {
  display: inline;
  vertical-align: middle;
}

#temperature {
  font-size: 60px;
  font-weight: 800;
  margin-right: 5px;
}

#celsius {
  margin-right: 10px;
}

#fahrenheit {
  margin-right: 5px;
  color: #b0bec5;
}

#celsius,
#temp-divider,
#fahrenheit {
  font-size: 30px;
  font-weight: 800;
}

#celsius:hover,
#fahrenheit:hover {
  cursor: pointer;
}

/* Bottom-Right CSS */

.other-details-key {
  float: left;
  font-size: 16px;
  font-weight: 300;
}

.other-details-values {
  float: left;
  font-size: 16px;
  font-weight: 400;
  margin-left: 40px;
}
.container {
  width: 80%;
  margin: 0 auto;
  padding: 20px;
}
.header {
  background-color: #252525;
  color: #fff;
  text-align: center;
  padding: 20px;
  border-radius: 30px;
}

h1 {
  margin: 0;
}

.search-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.searchbar {
  position: relative;
  width: 50%;
}

input[type="text"] {
  width: 50%;
  height: 30px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  outline: none;
  font-size: 16px;
}

.btn-search {
  background-color: #28a745;
  color: #fff;
  border: 1px solid #28a745;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  margin-left: 10px;
  transition: background-color 0.3s ease;
}

.btn-search:hover {
  background-color: #218838;
  border: 1px solid #218838;
}
</style>
