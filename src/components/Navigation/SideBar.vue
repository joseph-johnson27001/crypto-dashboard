<template>
  <div :class="['sidebar', { collapsed }]">
    <div class="sidebar-title">
      <h1 v-if="!collapsed">Crypto Exchange</h1>
      <i class="fas fa-bars" @click="toggleCollapse"></i>
    </div>
    <ul>
      <li
        v-for="(item, index) in menuItems"
        :key="index"
        :class="{
          active: activeItem === item.name,
          'logout-item': item.name === 'logout',
        }"
        @click="setActiveItem(item.name)"
      >
        <div class="icon-container">
          <i :class="item.icon"></i>
        </div>
        <span v-if="!collapsed">{{ item.label }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  props: {
    collapsed: Boolean,
  },
  emits: ["update:collapsed"],
  data() {
    return {
      activeItem: "dashboard",
      menuItems: [
        {
          name: "dashboard",
          label: "Dashboard",
          icon: "fas fa-home",
          link: "/",
        },
        {
          name: "portfolio",
          label: "Portfolio",
          icon: "fas fa-wallet",
          link: "/portfolio",
        },
        {
          name: "markets",
          label: "Markets",
          icon: "fas fa-chart-line",
          link: "/markets",
        },
        {
          name: "watchlist",
          label: "Watchlist",
          icon: "fas fa-star",
          link: "/watchlist",
        },
        {
          name: "news",
          label: "News",
          icon: "fas fa-newspaper",
          link: "/news",
        },
        {
          name: "alerts",
          label: "Alerts",
          icon: "fas fa-bell",
          link: "/alerts",
        },
        {
          name: "settings",
          label: "Settings",
          icon: "fas fa-cog",
          link: "/settings",
        },
      ],
    };
  },
  methods: {
    toggleCollapse() {
      this.$emit("update:collapsed", !this.collapsed); // ✅ emit instead of mutate
    },
    setActiveItem(name) {
      this.activeItem = name;
    },
  },
};
</script>

<style scoped>
.sidebar {
  width: 280px;
  color: #c1bfd6;
  height: 100%;
  max-height: 100vh;
  position: relative;
  z-index: 10;
  font-size: 15px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: width 0.3s ease;
  overflow-y: scroll;
  scrollbar-width: none;
  flex-shrink: 0;
  font-family: "Rajdhani", sans-serif;
  border-right: 1px solid rgba(193, 191, 214, 0.5);
}

.sidebar.collapsed {
  width: 80px;
  padding-top: 10px;
}

.sidebar-title {
  padding: 20px 20px 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sidebar-title h1 {
  font-weight: 400;
  margin: 0;
  color: orange;
  font-size: 1.8rem;
  letter-spacing: -1px;
  flex-wrap: nowrap;
  white-space: nowrap;
}

.sidebar-title i {
  cursor: pointer;
  font-size: 22px;
}

.sidebar ul {
  list-style: none;
  padding: 0;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.sidebar ul li {
  padding: 20px 10px;
  cursor: pointer;
  display: flex;
  align-items: center;
  white-space: nowrap;
  font-size: 1.15rem;
}

.sidebar.collapsed .icon-container {
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.sidebar ul li.logout-item {
  margin-top: auto;
}

.sidebar ul li:hover {
  background: #2e3348;
}

.sidebar ul li.active {
  background: #2e3348;
  color: white;
}

.sidebar ul li i {
  margin-right: 12px;
  margin-left: 5px;
  color: #c1bfd6;
}

.sidebar ul li.active i {
  color: orange;
}

.sidebar.collapsed ul li,
.sidebar.collapsed .sidebar-title {
  justify-content: center;
}

.sidebar.collapsed ul li i {
  margin: 0;
  padding: 10px;
  font-size: 18px;
}

@media (max-width: 699px) {
  .sidebar,
  .sidebar.collapsed {
    display: none;
  }
}
</style>
