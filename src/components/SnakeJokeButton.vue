<template>
  <!-- calls the display_snake_joke function when generate joke is clicked  -->
  <div><button @click="display_snake_joke">display snake</button></div>
</template>

<script>
// making a variable to use and setting it to undefined
export default {
  data() {
    return {
      joke: undefined,
    };
  },
  // function that will replace all the spaces with _ and set it as the variable joke
  methods: {
    snake_joke(joke) {
      this.joke = joke.replaceAll(" ", "_");
    },
    // function that emits the joke variable that can be called using the came snake
    display_snake_joke() {
      this.$root.$emit(`snake`, this.joke);
    },
  },
  // gets the info from the emit joke clicked and runs the function snake_joke
  mounted() {
    this.$root.$on(`joke_clicked`, this.snake_joke);
  },
};
</script>

<style scoped>
</style>