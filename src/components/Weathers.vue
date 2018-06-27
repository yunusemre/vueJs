<template>
  	<div class="weather">
        <loader v-bind:load="!loading" />
        <div class="weather--data" v-if="loading">
          <img class="weather--data__img" v-bind:src="'https://openweathermap.org/img/w/' + data.weather[0].icon + '.png'" alt="data.name" width="50" height="50">
          {{data.name}} / {{data.wind.speed}}

          <sub-weather v-bind:name="data.name" v-bind:code="data.sys.country"/>
        </div>
    </div>
</template>

<script>
import SubWeather from "./SubWeather";
import Loader from "./Loading";
import axios from "axios";

export default {
  name: "Weathers",
  props: ["city"],
  components: { SubWeather, Loader },
  data() {
    return {
      data: {},
      loading: false
    };
  },
  methods: {
    getWeather() {
      axios
        .get(
          `http://api.openweathermap.org/data/2.5/weather?q=${
            this.city
          }&APPID=b712b9a9b0785a9842d7c7ba49f37a5f`
        )
        .then(response => {
          this.data = response.data;
        })
        .finally(res => {
          this.loading = true;
        }); 
    }
  },
  created() {
    setInterval(() => {
      this.getWeather();
    }, 500);
  }
};
</script>
