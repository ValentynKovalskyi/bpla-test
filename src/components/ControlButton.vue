<template>
  <button
          id="mainButton"
          :class="{'start': this.state === 'start','stop': this.state === 'stop'}">
      {{ text }}
  </button>
</template>

<script>
export default {
  name: "ControlButton",
  props: ["state"],
  data() {
    return {
      startText: "Почати",
      stopText: "Зупинити",
    }
  },
  computed: {
    text() {
      if (this.state === "start") return this.startText;
      else if (this.state === "stop") return this.stopText
      else return 'Invalid State'
    }
  }
}
</script>

<style>
#mainButton {
    position: absolute;
    left: 50vw;
    bottom: 10vh;
    padding: 1em 2em;
    border-radius: 1em;
    font-size: larger;
}
#mainButton:hover {
    cursor: pointer;
}

.start {
    background-color: yellow;
    color: black;
}

.stop {
    background-color: black;
    color: white;
}
</style>