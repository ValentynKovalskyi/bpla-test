<template>
  <div id="fieldContainer">
      <ControlButton :state="state" @click="execute"/>
      <PlaneObject
              :direction="planeState.direction"
              :left="planeState.left"
              :top="planeState.top"
      />
  </div>
</template>

<script>
import ControlButton from "@/components/ControlButton.vue";
import PlaneObject from "@/components/PlaneObject.vue";

export default {
  name: "FieldView",
  components: { PlaneObject, ControlButton },
  props: [
    'data',
  ],
  data() {
    return {
      state: "start",
      process: null,
      planeState: {
        direction: 90,
        left: 50,
        top: 50,
        speed: 0,
      }
    }
  },
  methods: {
    toggleState () {
      this.state === "start" ? this.state = "stop": this.state = "start"
    },
    execute () {
      this.toggleState();
      console.log(this.state);
      if(this.state === "stop") {
        let stateIndex = 0;
        const interval = 20_000 / this.data.length;
        this.process = setInterval(() => {
          if(this.data[stateIndex]) {
            this.planeState.direction = this.data[stateIndex].direction;
            const distance = this.data[stateIndex].speed * 0.002;

            const deltaX = distance * Math.sin((this.planeState.direction * Math.PI) / 180);
            const deltaY = distance * Math.cos((this.planeState.direction * Math.PI) / 180);

            this.planeState.left += deltaX;
            this.planeState.top -= deltaY;
            ++stateIndex;
          } else {
            clearInterval(this.process);
          }
        }, interval);
      } else {
        clearInterval(this.process);
        this.resetPlaneState();
      }
    },
    resetPlaneState () {
      this.planeState = {
        direction: 0,
        left: 50,
        top: 50,
        speed: 0,
      };
    }
  },
}
</script>

<style scoped>
#fieldContainer {
    background-image: url("../assets/fieldImg.png");
    height: 100vh;
    width: 100vw;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>