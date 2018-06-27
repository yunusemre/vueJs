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
        "İstanbul,tr",
        "Madrid,es",
        "Nantes,fr",
        "Berlin,de"
      ]
    };
  },
  created() {
    // axios.get(`https://owm.io/data/2.5/find?lat=51&lon=7.5&cnt=5&appid=b712b9a9b0785a9842d7c7ba49f37a5f`)
    // .then(res=> this.city = res.data)
  }
};
</script>

<style lang="scss">
  body {
    font-family: 'Noto Sans', sans-serif;
    margin-top: 20px;
    font-size: 12px;
    line-height: 18px;
    padding-left: env(safe-area-inset-left);
    padding-right: env(safe-area-inset-right);
  }
  .weather-app{
    width: 80%;
    align-items: center;
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    margin: 0 auto;

    @media screen and (max-width: 768px){
      flex-direction: column;
    }
  }
</style>

