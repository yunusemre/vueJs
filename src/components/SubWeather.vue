<template>
  	<div class="sub-weather">
        <loader v-if="!loading" />
        <div v-if="loading" class="sub-weather__box" v-for="item in data" :key="item.dt">
            <p class="sub-weather__box--date">{{convertDate(item.dt)}}</p>
            <p class="sub-weather__box--temp">{{item.temp.day}} °C </p>
            <p class="sub-weather__box--speed">{{item.speed}}</p>
            <img class="sub-weather__box--images" v-bind:src="'https://openweathermap.org/img/w/' + item.weather[0].icon + '.png'" alt="data.name" width="50" height="50">
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
        .get(`https://api.openweathermap.org/data/2.5/forecast/daily?q=${this.name},${this.code}&appid=b712b9a9b0785a9842d7c7ba49f37a5f&cnt=5&units=metric`)
        .then(response => {
          this.data = response.data.list;
          this.loading = true;
        })
    },

    convertDate(val) {
      return new Date(val * 1000).toLocaleDateString();
    }
  },
  created() {
    setTimeout(()=>{
      this.getSubWeather();
    }, 300)
  }
};
</script>

<style lang="scss">
  .sub-weather {
    font-family: 'Quicksand', serif;
    margin-top: 20px;
    text-align: left;
    width: 100%;

    &__box {
      border-bottom: 1px solid #81bedf;
      line-height: 18px;
      margin-top: 5px;
      padding: 5px;
      position: relative;

      &:last-child {
        border-bottom: 0;
      }

      &--images {
        position: absolute;
        right: 10px;
        top: 0px;
      }
    }
    
  }
</style>

