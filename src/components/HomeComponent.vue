<template>
  <main>
    <div class="search-box">
      <input
        v-model="query"
        @keypress="fetchWeather"
        type="text"
        class="search-bar"
        placeholder="Search.."
      />
    </div>

    <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
      <div class="location-box">
        <div class="location">
          {{ weather.name }}, {{ weather.sys.country }}
        </div>
        <div class="date">{{ dateBuilder() }}</div>

        <div class="weather-box">
          <div class="temp">{{ Math.round(weather.main.temp) }}°C</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      api_key: "f41ba71a687a7e883bbf4df15e2c525e",
      api_endpoint: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
    };
  },
  computed: {
    completeUrl() {
      return (
        this.api_endpoint +
        "weather?q=" +
        this.query +
        "&units=metric&APPID=" +
        this.api_key
      );
    },
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(this.completeUrl)
          .then((response) => {
            return response.json();
          })
          .then(this.setResults);
      }
    },

    setResults(results) {
      console.log(results);
      this.weather = results;
    },

    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>

<style scoped>
</style>