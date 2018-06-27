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
  .weather-app{
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    
  }
</style>

