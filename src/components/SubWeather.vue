<template>
  	<div class="sub--weather">
        <hr>
        <loader v-bind:load="!loading" />
        <div v-if="loading" class="sub--weather__data" v-for="item in data" :key="item.dt">
            {{convertDate(item.dt)}} - {{item.temp.min}}
            {{item.weather[0].main}}
            <img class="sub--weather__data__img" v-bind:src="'https://openweathermap.org/img/w/' + item.weather[0].icon + '.png'" alt="data.name" width="50" height="50">
        </div>
    </div>
</template>

<script>
import axios from "axios";
import Loader from "./Loading";
export default {
  name: "SubWeather",
  props: ["name", "code"],
  components: { Loader },
  data() {
    return {
      data: null,
      weather: null,
      loading: false
    };
  },
  methods: {
    getSubWeather() {
      axios
        .get(
          `http://api.openweathermap.org/data/2.5/forecast/daily?q=${
            this.name
          },${this.code}&appid=b712b9a9b0785a9842d7c7ba49f37a5f&cnt=5`
        )
        .then(response => {
          this.data = response.data.list;
        })
        .finally(res => {
          this.loading = true;
        });
    },

    convertDate(val) {
      return new Date(val * 1000).toLocaleDateString();
    }
  },
  created() {
    setInterval(() => {
      this.getSubWeather();
    }, 200);
  }
};
</script>
