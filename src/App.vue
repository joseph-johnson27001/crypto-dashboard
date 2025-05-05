<template>
  <div id="app">
    <SideBar />
    <div class="content"></div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";

export default {
  name: "App",
  components: {
    SideBar,
  },
};
</script>
<style>
body {
  background-color: #25293c;
  padding: 0;
  margin: 0;
  min-height: 100dvh;
}

#app {
  min-height: 100dvh;
  height: 100dvh;
}
</style>
