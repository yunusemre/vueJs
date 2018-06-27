<template>
  	<div class="loader">
      <img class="loader__img" src="https://openweathermap.org/themes/openweathermap/assets/img/img-loading.gif" width="50" height="50">
    </div>
</template>
<style lang="scss" scoped>
  .loader {
    position: relative;
    
    &__img {
      left: 45%;
      position: absolute;
      text-align: center;
      top: 10px;
    }
  }
</style>

