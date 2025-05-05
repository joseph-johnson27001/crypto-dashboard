<template>
  <div>
    <div class="top-nav">
      <div class="left-section">
        <span class="brand">Crypto Exchange</span>
      </div>
      <div class="right-section">
        <i class="fas fa-bars" @click="menuOpen = !menuOpen"></i>
      </div>
    </div>

    <transition name="fade">
      <ul v-if="menuOpen" class="dropdown-menu">
        <li
          v-for="item in menuItems"
          :key="item.name"
          @click="selectItem(item.name)"
        >
          <i :class="item.icon"></i>
          <span>{{ item.label }}</span>
        </li>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  name: "TopNavigation",
  data() {
    return {
      menuOpen: false,
      menuItems: [
        { name: "dashboard", label: "Dashboard", icon: "fas fa-home" },
        { name: "portfolio", label: "Portfolio", icon: "fas fa-wallet" },
        { name: "markets", label: "Markets", icon: "fas fa-chart-line" },
        { name: "watchlist", label: "Watchlist", icon: "fas fa-star" },
        { name: "news", label: "News", icon: "fas fa-newspaper" },
        { name: "alerts", label: "Alerts", icon: "fas fa-bell" },
        { name: "settings", label: "Settings", icon: "fas fa-cog" },
      ],
    };
  },
  methods: {
    selectItem() {
      this.menuOpen = false;
    },
  },
};
</script>

<style scoped>
.top-nav {
  display: none;
  background-color: #2e3348;
  color: #c1bfd6;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid rgba(193, 191, 214, 0.2);
  font-family: "Rajdhani", sans-serif;
  width: 100%;
  height: 40px;
  margin-bottom: 20px;
  margin-left: -20px;
  margin-right: -20px;
  margin-top: -20px;
  width: 100dvw;
  padding-top: 10px;
  height: 50px;
}

.left-section {
  display: flex;
  align-items: center;
  padding-left: 20px;
}

.left-section i {
  font-size: 20px;
  cursor: pointer;
  color: orange;
}

.brand {
  font-size: 1.25rem;
  color: orange;
  font-weight: 500;
}

.right-section i {
  font-size: 20px;
  cursor: pointer;
  padding-right: 20px;
}

@media (max-width: 699px) {
  .top-nav {
    display: flex;
  }
}

.dropdown-menu {
  display: flex;
  flex-direction: column;
  background: #1f2333;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  list-style: none;
  padding: 0;
  margin: 0;
  margin-top: -20px;
  margin-left: -20px;
  width: 100dvw;
  color: #c1bfd6;
  z-index: 99;
  margin-bottom: 20px;
}

ul {
  border-bottom: 1px solid rgba(193, 191, 214, 0.2);
}

.dropdown-menu li {
  padding: 0.75rem 1rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background 0.1s linear;
}

.dropdown-menu li:hover {
  background: rgba(255, 255, 255, 0.05);
}

.dropdown-menu i {
  color: orange;
  width: 20px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.1s linear;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
