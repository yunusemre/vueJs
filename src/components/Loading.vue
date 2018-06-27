<template>
  	<div class="load">
        <div v-if="load">
          <img class="load--img" src="https://openweathermap.org/themes/openweathermap/assets/img/img-loading.gif" width="20" height="20">
        </div>
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
  .load {
    position: relative;
    width: 100%; 
    &--img {
      position: absolute;
      top: 10px;
      left: 45%;
      text-align: center;
    }
  }
</style>

