<template>
  <div><button @click="display_snake_joke">display snake</button></div>
</template>

<script>
export default {
  data() {
    return {
      joke: undefined,
    };
  },

  methods: {
    snake_joke(joke) {
      this.joke = joke.replaceAll(" ", "_");
    },

    display_snake_joke() {
      this.$root.$emit(`snake`, this.joke);
    },
  },

  mounted() {
    this.$root.$on(`joke_clicked`, this.snake_joke);
  },
};
</script>

<style scoped>
</style>