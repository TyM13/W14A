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

    change_joke_loud(handle_loud) {
      this.joke = handle_loud;
    },

    change_joke_snake(handle_snake) {
      this.joke = handle_snake;
    },
    change_joke_normal(handle_normal) {
      this.joke = handle_normal;
    },
  },
  mounted() {
    this.$root.$on(`loud`, this.change_joke_loud),
      this.$root.$on(`snake`, this.change_joke_snake),
      this.$root.$on(`normal`, this.change_joke_normal);
  },
};
</script>

<style scoped>
</style>