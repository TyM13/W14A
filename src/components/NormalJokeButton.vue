<template>
  <div>
    <!-- calls the display_normal_joke function when generate joke is clicked -->
    <button @click="display_normal_joke">display normal</button>
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
    normal_joke(joke) {
      this.joke = joke;
    },
    // // function that emits the joke variable that can be called using the came snake
    display_normal_joke() {
      this.$root.$emit(`normal`, this.joke);
    },
  },
  // gets the info from the emit joke clicked and runs the function normal_joke
  mounted() {
    this.$root.$on(`joke_clicked`, this.normal_joke);
  },
};
</script>

<style scoped>
</style>