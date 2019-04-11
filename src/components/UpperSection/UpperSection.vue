<template>
  <div>
    <Header/>
    <NavBar @audioArrIndex="passIndexToParent"/>
  </div>
</template>

<script>
import Header from "./Header";
import NavBar from "./NavBar";

export default {
  name: "UpperSection",
  components: {
    Header,
    NavBar
  },
  methods: {
    passIndexToParent(val) {
      this.$emit("audioArrIndex", val);
    }
  }
};
</script>
