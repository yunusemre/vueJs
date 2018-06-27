<template>
  	<div class="weather">
        <div class="weather__data" v-if="loading" @click="this.showWeathersDetail">
          <div class="weather__data__info">
            <img class="weather__data__info__img" v-bind:src="'https://openweathermap.org/img/w/' + data.weather[0].icon + '.png'" alt="data.name" width="80" height="80">
            <section class="weather__data__info--box">
              <p class="weather__data__info--box__name">{{data.name}}</p>
              <p class="weather__data__info--box__wine">Wind: {{data.wind.speed}}</p>
              <p class="weather__data__info--box__wine">Temp: {{data.main.temp}} °C</p>
            </section>
          </div>
        </div>
        <sub-weather v-if="toggle" v-bind:name="data.name" v-bind:code="data.sys.country"/>
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
        .get(`http://api.openweathermap.org/data/2.5/weather?q=${this.city}&APPID=b712b9a9b0785a9842d7c7ba49f37a5f&units=metric`)
        .then(response => {
          this.data = response.data;
        })
        .finally(res => {
          this.loading = true;
        }); 
    },
    
    showWeathersDetail(city){
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
    width: 20%;
    border: 1px solid #eee;
    border-radius: 4px;
    cursor: pointer;
    min-height: 100px;
    position: relative;
    text-align: center;

    @media screen and (max-width: 768px){
      width: 100%;
    }


    &__data {

      &__info {
        &__img {
          text-align: center;
        }

        &--box{
          &__name {
            font-size: 16px;
          }
        }
      }
  }

}
</style>

