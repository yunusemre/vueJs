<template>
  	<div class="weather" v-bind:class="{ active: toggle }">
        <div class="weather__data" v-if="loading" @click="this.showWeathersDetail">
          <div class="weather__data__info">
            <p class="weather__data__info--name">{{data.name}}</p>
            <p class="weather__data__info--temp">{{data.main.temp}}°</p>
            <img class="weather__data__info--img" v-bind:src="'https://openweathermap.org/img/w/' + data.weather[0].icon + '.png'" alt="data.name">
            <p class="weather__data__info--speed">wind speed: {{data.wind.speed}}</p>
          </div>
        </div>
        <sub-weather v-if="toggle" v-bind:name="data.name" v-bind:code="data.sys.country"/>
    </div>
</template>

<script>
import SubWeather from "./SubWeather";
import axios from "axios";

export default {
  name: "Weathers",
  props: ["city"],
  components: { SubWeather },
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
    &:hover {
      background-color: #679ebb;  
      transition: .5s ease; 
    }
    &.active {
      background-color: #6295b1;  
    }
    background-color: #71aac9;
    border-radius: 10px;
    cursor: pointer;
    min-height: 100px;
    margin: 0 0 5px 5px;
    text-align: center;
    width: 20%;

    @media screen and (max-width: 768px){
      width: 100%;
    }
    &__data {
      &__info {
        margin-top: 20px;
        &--img {
          margin-top: 5px;
          text-align: center;
        }
        &--name {
          font-size: 16px;
        }
        &--temp {
          font-family: 'Quicksand', serif;
          font-size: 42px;
          font-weight: 100;
          margin: 10px 0 5px 0;
        }
        &--speed {
          margin: 10px 0;
        }
      }
  }

}
</style>

