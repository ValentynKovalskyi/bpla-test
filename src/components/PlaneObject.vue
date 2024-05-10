<template>
  <img ref="planeObject" id="planeObject" src="../assets/plane.png">
</template>
<script>

export default {
  name: "PlaneObject",
  props: {
    direction: {
      type: Number,
      default: 0,
    },
    left: {
      type: Number,
      default: 50,
    },
    top: {
      type: Number,
      default: 50,
    }
  },
  watch: {
    left(newLeft) {
      this.$refs.planeObject.style.left = newLeft + "vw";
    },
    top(newTop) {
      this.$refs.planeObject.style.top = newTop + "vh";
    },
    direction(newDirection) {
      this.$refs.planeObject.style.rotate = newDirection + "deg";
    }
  },
  mounted() {
    this.$refs.planeObject.style.left = this.left + "vw";
    this.$refs.planeObject.style.top = this.top + "vh";
  }
}
</script>

<style>
#planeObject {
    position: absolute;
    height: 2vh;
    width: 1vw;
    transition: top 1000ms, left 1000ms, rotate 100ms;
}
</style>