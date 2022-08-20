<template>
  <div>
    <button @click="show_normal_joke">Generate Joke</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  mounted() {},
  methods: {
    show_normal_joke(details) {
      axios
        .request({
          url: `https://ron-swanson-quotes.herokuapp.com/v2/quotes`,
        })
        .then((response) => {
          response;
          details;
        })
        .catch((error) => {
          error;
        });
    },
  },
};
</script>

<style scoped>
</style>