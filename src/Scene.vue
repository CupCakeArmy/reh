<template>
  <div class="scene" ref="scene">
    <div class="container">
      <img :src="this.d.bg" class="bg" ref="bg"/>
      <Sprite v-for="sprite in d.sprites" v-bind:key="sprite.image" v-bind:d="sprite"/>
    </div>
  </div>
</template>

<script>
const FastAverageColor = require("fast-average-color");
import Sprite from "./Sprite";

const fac = new FastAverageColor();

export default {
  name: "scene",
  components: { Sprite },
  props: ["d"],
  methods: {
    color() {
      fac.getColorAsync(this.$refs.bg, color => {
        this.$refs.scene.style.backgroundColor = color.hex;
      });
    }
  },
  mounted() {
    this.color();
  },
  updated() {
    this.color();
  }
};
</script>

<style scoped>
.scene {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 100%;
  background-color: #eeeeee;
}

.bg {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.container {
  height: 95vmin;
  width: 95vmin;
  background: white;
  overflow: hidden;
  z-index: 1;
  position: relative;
}
</style>
