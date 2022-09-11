<template>
  <div>
    <!-- calls the display_loud_joke function when generate joke is clicked  -->
    <button @click="display_loud_joke">display loud</button>
  </div>
</template>

<script>
// making a variable to use and setting it to undefined
export default {
  data() {
    return {
      joke: undefined,
    };
  },
  //
  methods: {
    loud_joke(joke) {
      this.joke = joke.toUpperCase();
    },
    // // function that emits the joke variable that can be called using the came snake
    display_loud_joke() {
      this.$root.$emit(`loud`, this.joke);
    },
  },
  // gets the info from the emit joke clicked and runs the function loud_joke
  mounted() {
    this.$root.$on(`joke_clicked`, this.loud_joke);
  },
};
</script>

<style scoped>
</style>