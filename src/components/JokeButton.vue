<template>
  <div>
    <!-- display's what the variable joke is equal to
    calls the show_joke function when generate joke is clicked -->
    <h1 ref="joke_container">{{ joke }}</h1>
    <button @click="show_joke">Generate Joke</button>
  </div>
</template>

<script>
// making a variable to use and setting it to undefined
import axios from "axios";
export default {
  data() {
    return {
      joke: undefined,
    };
  },

  methods: {
    // requests a joke from the api when the button is clicked and sets response[`data`][0]; to the variable joke as well as
    // emitting the joke info so it can be changed used by other components
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
    // function that uses the info from the component loud joke, sets the handle_loud as the variable joke
    change_joke_loud(handle_loud) {
      this.joke = handle_loud;
    },
    // function that uses the info from the component snake joke, sets the handle_loud as the variable joke
    change_joke_snake(handle_snake) {
      this.joke = handle_snake;
    },
    // function that uses the info from the component normal joke, sets the handle_loud as the variable joke
    change_joke_normal(handle_normal) {
      this.joke = handle_normal;
    },
  },
  // when everything is loaded on the page it will run the function that's called.
  mounted() {
    this.$root.$on(`loud`, this.change_joke_loud),
      this.$root.$on(`snake`, this.change_joke_snake),
      this.$root.$on(`normal`, this.change_joke_normal);
  },
};
</script>

<style scoped>
</style>