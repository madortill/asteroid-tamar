<template>
  <div id="app">
    <div class="background">
      <info-asteroid v-if="showPage === 1"></info-asteroid>
      <type-of-asteroid v-else-if="showPage === 2"></type-of-asteroid>
      <game v-else></game>
    </div>
  </div>
</template>

<script>
import Game from './components/Game.vue';
import InfoAsteroid from './components/InfoAsteroid.vue';
import TypeOfAsteroid from './components/TypeOfAsteroid.vue';

  export default {
    name: "app",
    components: {
      Game,
      InfoAsteroid,
      TypeOfAsteroid
    },
    data() {
      return {
        showPage: 3,
      }
    },
    methods: {

    }
  }
</script>

<style>
  html,
  body {
    margin: 0;
    overflow: hidden;
    direction: rtl;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  html {
    font-size: calc(16px + 1vh);
    height: 100%;
  }

  .background {
    height: calc(var(--vh, 1vh) * 100);
    width: 100vw;
    background-image: url("@/assets/background.svg");
    background-size: 100vw 100vh;
    background-repeat: no-repeat;
  }

</style>
