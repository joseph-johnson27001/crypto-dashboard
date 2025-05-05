<template>
  <div id="app">
    <SideBar v-model:collapsed="isSidebarCollapsed" />
    <div class="content">
      <DashboardPage />
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import DashboardPage from "./views/DashboardPage.vue";

export default {
  name: "App",
  components: {
    SideBar,
    DashboardPage,
  },
  data() {
    return {
      isSidebarCollapsed: true,
    };
  },
  watch: {
    isSidebarCollapsed() {
      setTimeout(() => {
        this.triggerResize();
      }, 100);
    },
  },
  methods: {
    triggerResize() {
      window.dispatchEvent(new Event("resize"));
    },
  },
};
</script>

<style>
body {
  background-color: #25293c;
  padding: 0;
  margin: 0;
  min-height: 100dvh;
  font-family: "Rajdhani", sans-serif;
  overflow: hidden;
}

#app {
  display: flex;
  min-height: 100dvh;
  height: 100dvh;
  width: 100%;
}

.content {
  padding: 1.5rem;
  width: 100%;
  overflow-y: scroll;
  scrollbar-width: none;
}
</style>
