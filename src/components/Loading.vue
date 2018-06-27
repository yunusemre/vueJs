<template>
  	<div class="load">
        <div v-if="load">Loading...</div>
    </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Loader",
  props: ["load"]
};
</script>
