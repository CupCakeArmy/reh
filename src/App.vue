<template>
  <div class="app">
    <Scene v-if="current" v-bind:d="current"/>
  </div>
</template>

<script>
import Scene from "./Scene";
import Scenes from "./scenes/index.js";

export default {
  name: "app",
  components: { Scene },
  data() {
    return {
      index: 0
    };
  },
  computed: {
    current() {
      return Scenes[this.index];
    }
  },
  methods: {
    next() {
      const n = this.index + 1;
      this.index = n >= Scenes.length ? 0 : n;
    }
  },
  created() {
    const interval = setInterval(this.next, 3000);
  }
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;
}
</style>
