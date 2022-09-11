<template>
  <div>
    <button @click="display_normal_joke">display normal</button>
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
    normal_joke(joke) {
      this.joke = joke;
    },

    display_normal_joke() {
      this.$root.$emit(`normal`, this.joke);
    },
  },

  mounted() {
    this.$root.$on(`joke_clicked`, this.normal_joke);
  },
};
</script>

<style scoped>
</style>