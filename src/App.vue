<template>
  <div id="app" @click.once="keyboarShortcutsMessage">
    <UpperSection @audioArrIndex="getIndexFromChild"/>
    <LowerSection :audioArrIndex="index"/>
  </div>
</template>

<script>
import UpperSection from "./components/UpperSection/UpperSection.vue";
import LowerSection from "./components/LowerSection/LowerSection";

export default {
  name: "app",
  components: {
    UpperSection,
    LowerSection
  },
  data() {
    return {
      index: 0,
      isPC: !/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(
        navigator.userAgent
      )
    };
  },
  methods: {
    getIndexFromChild(val) {
      this.index = val;
    },
    keyboarShortcutsMessage() {
      if (this.isPC) {
        alert(`Keyboar shortcuts:
      Space: play/pause
      Arrow Up: icrease Volume
      Arrow Down: decrease Volume
      Right Arrow: move Forward
      Left Arrow: move Backward
      M: mute`);
      }
    }
  }
};
</script>

<style lang="scss">
html,
body,
p {
  margin: 0;
  padding: 0;
}

html {
  background-color: black;
  margin: 1%;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>