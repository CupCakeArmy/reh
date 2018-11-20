<template>
<div class="sprite" :style="style">
  <img :src="d.image" />
  </div>
</template>

<script>
export default {
  name: "sprite",
  props: ["d"],
  computed: {
    style() {
      return `top: ${this.d.y}%; left: ${this.d.x}%; transform: scale(${
        this.d.scale
      }) rotate(${this.d.rot}deg);`;
    }
  }
};
</script>

<style scoped>
.sprite {
  z-index: 2;
  position: absolute;
  height: 50%;
  width: 50%;
}

img {
  animation: wiggle 1.5s linear 0s infinite;
  height: 100%;
  width: 100%;
}

@keyframes wiggle {
  0%,
  100% {
    transform: rotate(0deg);
  }

  25% {
    transform: rotate(-2deg);
  }

  75% {
    transform: rotate(2deg);
  }
}
</style>
