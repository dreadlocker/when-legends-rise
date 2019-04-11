<template>
  <div>
    <p v-for="(textRow, index) in lyricsArr[key]" :key="index">
      {{textRow || '&nbsp;'}} 
    </p>
  </div>
</template>

<script>
import { songsObj } from "../../assets/lyricsObj.js";

export default {
  name: "Lyrics",
  props: {
    audioArrIndex: Number
  },
  data() {
    return {
      key: "song1Lyrics",
      lyricsArr: []
    };
  },
  mounted() {
    this.lyricsArr = songsObj;
  },
  watch: {
    audioArrIndex: function() {
      this.key = `song${this.audioArrIndex + 1}Lyrics`;
    }
  },
};
</script>

<style lang="scss" scoped>
p {
  color: #858282;
}
</style>