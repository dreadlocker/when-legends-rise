<template>
  <div id="nav">
    <div
      v-for="(title, index) in songsTitleArr"
      @click="changeSong"
      :id="index"
      :class="index === currentElmentID ? 'navElement clicked' : 'navElement'"
      :key="index"
    >&nbsp;{{title}}&nbsp;</div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      currentElmentID: 0,
      songsTitleArr: [
        "1.When legends rise",
        "2.Bulletproof",
        "3.Unforgettable",
        "4.Every part of me",
        "5.Take it to the edge",
        "6.Under your scars",
        "7.Someday",
        "8.Just one time",
        "9.Say my name",
        "10.Let it out",
        "11.Eye of the storm"
      ]
    };
  },
  methods: {
    changeSong(e) {
      this.currentElmentID = +e.target.id;
      this.$emit("audioArrIndex", +e.target.id);
    }
  }
};
</script>

<style lang="scss" scoped>
#nav {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 1rem;
  color: rgb(133, 130, 130);
}

.navElement {
  cursor: pointer;
  &:hover {
    background-color: #343109;
  }
  &:active {
    transform: scale(0.9);
  }
}

.clicked {
  color: #c0c0c0;
}
</style>