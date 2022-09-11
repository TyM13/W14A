<template>
  <div>
    <button @click="display_loud_joke">display loud</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      joke: undefined,
    };
  },

  methods: {
    loud_joke(joke) {
      this.joke = joke.toUpperCase();
    },

    display_loud_joke() {
      this.$root.$emit(`loud`, this.joke);
    },
  },

  mounted() {
    this.$root.$on(`joke_clicked`, this.loud_joke);
  },
};
</script>

<style scoped>
</style>