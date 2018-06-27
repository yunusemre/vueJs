<template>
  	<div class="loader">
      <img class="loader__img" src="https://openweathermap.org/themes/openweathermap/assets/img/img-loading.gif" width="50" height="50">
    </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Loader",
  props: ["load"]
};
</script>

<style lang="scss" scoped>
  .loader {
    position: absolute;
    
    &__img {
      left: 45%;
      position: absolute;
      text-align: center;
      top: 10px;
      width: 100%; 
    }
  }
</style>

