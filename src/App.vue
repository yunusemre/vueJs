<template>
  <div class="weather-app">
      <weathers v-for="item in cities" :key="item" v-bind:city="item" />
  </div>
</template>

<script>
import axios from "axios";
import Weathers from "./components/Weathers";
export default {
  name: "app",
  components: {
    Weathers
  },
  data() {
    return {
      cities: [
        "London,uk",
        "Kiev,ua",
        "Madrid,es",
        "Nantes,fr",
        "Berlin,de"
      ]
    };
  },
  created() {
    // axios.get(`https://owm.io/data/2.5/find?lat=51&lon=7.5&cnt=5&appid=b712b9a9b0785a9842d7c7ba49f37a5f`)
    // .then(res=> this.cities = res.data)
  }
};
</script>

<style lang="scss">
  body {
    font-family: 'Josefin Slab', sans-serif;
    margin-top: 20px;
    font-size: 12px;
    padding-left: env(safe-area-inset-left);
    padding-right: env(safe-area-inset-right);
    background-color: #81bedf;
    background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%2371aac9' fill-opacity='0.37' fill-rule='evenodd'/%3E%3C/svg%3E");
  }
  .weather-app{
    width: 90%;
    align-items: center;
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    margin: 0 auto;

    @media screen and (max-width: 768px){
      flex-direction: column;
      width: 100%;
    }
  }
</style>

