<template>
  <div>
    <audio id="audio" ref="player" controls>
      <source :src="reuslt">
    </audio>
  </div>
</template>

<script>
export default {
  name: "AudioPlayer",
  props: {
    audioArrIndex: Number
  },
  data() {
    return {
      reuslt: "",
      srcArr: [
        require("../../assets/Songs/Godsmack - When legends rise.mp3"),
        require("../../assets/Songs/Godsmack - Bulletproof.mp3"),
        require("../../assets/Songs/Godsmack - Unforgettable.mp3"),
        require("../../assets/Songs/Godsmack - Every part of me.mp3"),
        require("../../assets/Songs/Godsmack - Take it to the edge.mp3"),
        require("../../assets/Songs/Godsmack - Under your scars.mp3"),
        require("../../assets/Songs/Godsmack - Someday.mp3"),
        require("../../assets/Songs/Godsmack - Just one time.mp3"),
        require("../../assets/Songs/Godsmack - Say my name.mp3"),
        require("../../assets/Songs/Godsmack - Let it out.mp3"),
        require("../../assets/Songs/Godsmack - Eye of the storm.mp3")
      ]
    };
  },
  mounted() {
    this.reuslt = this.srcArr[0];
  },
  watch: {
    audioArrIndex: function() {
      this.reuslt = this.srcArr[this.audioArrIndex];
      this.$refs.player.load();
    }
  },
  created: function() {
    // Keyboar shortcuts for PC
    window.addEventListener("keyup", this.keyboardEvent);
  },
  methods: {
    keyboardEvent(e) {
      const keyCodes = [32, 37, 38, 39, 40, 77];
      if(!keyCodes.includes(e.keyCode))return;
      return {
        // playPause
        [keyCodes[0]]: () => (this.$refs.player.paused) ? this.$refs.player.play() : this.$refs.player.pause(),
        // moveBackward
        [keyCodes[1]]: () => (this.$refs.player.currentTime >= 5) ? this.$refs.player.currentTime -= 5 : '',
        // volumeUp
        [keyCodes[2]]: () => (this.$refs.player.volume < 1) ? this.$refs.player.volume += 0.1 : '',
        // volumeDown
        [keyCodes[3]]: () => (this.$refs.player.currentTime <= this.$refs.player.duration) ? this.$refs.player.currentTime += 5 : '',
        // mute
        [keyCodes[4]]: () => (this.$refs.player.volume > 0.01) ? this.$refs.player.volume -= 0.1 : '',
        // moveForward
        [keyCodes[5]]: () => (this.$refs.player.muted === true) ? this.$refs.player.muted = false : audio.muted = true,
      }[e.keyCode]();
    },
    asd() {
      console.log('object');
    }
  },
  destroyed: function() {
    window.removeEventListener("keyup", this.keyboardEvent);
  },
};
</script>

<style lang="scss" scoped>
#audio {
  width: 100%;
  margin-bottom: 1rem;
}
</style>