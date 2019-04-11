<template>
  <div>
    <AudioPlayer :audioArrIndex="audioArrIndex"/>
    <Lyrics :audioArrIndex="audioArrIndex"/>
  </div>
</template>

<script>
import AudioPlayer from "./AudioPlayer";
import Lyrics from "./Lyrics";

export default {
  name: "LowerSection",
  components: {
    AudioPlayer,
    Lyrics
  },
  props: {
    audioArrIndex: Number
  },
};
</script>