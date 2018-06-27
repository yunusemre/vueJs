<template>
  	<div class="weather">
        <loader v-bind:load="!loading" />
        <div class="weather--data" v-if="loading" @click="this.showWeathersDetail">
          <div class="weather--data__info">
            <img class="weather--data__info__img" v-bind:src="'https://openweathermap.org/img/w/' + data.weather[0].icon + '.png'" alt="data.name" width="50" height="50">
            {{convertDate(data.dt)}} - {{data.name}} sky is <span v-for="item in data.weather" :key="item.id">{{item.description}}</span>  
          </div>
          <sub-weather v-if="toggle" v-bind:name="data.name" v-bind:code="data.sys.country"/>
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
      loading: false,
      toggle: false
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
    },
    
    showWeathersDetail(){
      this.toggle = !this.toggle
    },

    convertDate(val) {
      return new Date(val * 1000).toLocaleDateString();
    }
  },
  created() {
    this.getWeather();
  }
};
</script>
<style lang="scss" scoped>
  .weather {
    min-height: 100px;
    border-top: 1px solid #ddd;
    background-color: #fff;

    &:nth-child(even) {
      background: #eee;
    }
    &--data__info {
      cursor: pointer;

      &__img {
      }
    }
}
</style>

