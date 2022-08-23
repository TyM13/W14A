<template>
  <div>
    <button @click="loud_joke">display loud</button>
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
  },

  mounted() {
    this.$root.$on(`joke_clicked`, this.loud_joke);
  },
};
</script>

<style scoped>
</style>