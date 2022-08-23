<template>
  <div>
    <h1 ref="joke_container">{{ joke }}</h1>
    <button @click="show_joke">Generate Joke</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: undefined,
    };
  },

  methods: {
    show_joke() {
      axios
        .request({
          url: `https://ron-swanson-quotes.herokuapp.com/v2/quotes`,
        })
        .then((response) => {
          this.joke = response[`data`][0];
          this.$root.$emit(`joke_clicked`, this.joke);
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