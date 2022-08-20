<template>
  <div id="app">
    <normal-joke-button></normal-joke-button>
    <snake-joke-button></snake-joke-button>
    <loud-joke-button></loud-joke-button>
    <joke-button></joke-button>
  </div>
</template>

<script>
import NormalJokeButton from "@/components/NormalJokeButton.vue";
import SnakeJokeButton from "@/components/SnakeJokeButton.vue";
import LoudJokeButton from "@/components/LoudJokeButton.vue";
import JokeButton from "@/components/JokeButton.vue";

export default {
  name: "App",
  components: {
    NormalJokeButton,
    SnakeJokeButton,
    LoudJokeButton,
    JokeButton,
  },
};
</script>

<style>
</style>
