<template>
  <div class="top-card-dark">
    <!-- Left Section -->
    <div class="search-area">
      <i class="fas fa-search"></i>
      <i class="fas fa-bars" @click="openMobileNav"></i>
      <input type="text" placeholder="Search..." />
    </div>

    <!-- Right Section -->
    <div class="icon-area">
      <i class="far fa-calendar-check"></i>
      <i class="far fa-comment-alt"></i>
      <i class="far fa-bell notification-icon">
        <span class="notification-dot"></span>
      </i>

      <div class="profile">
        <img src="https://randomuser.me/api/portraits/men/4.jpg" alt="User" />
        <span class="online-indicator"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopCard",
  methods: {
    openMobileNav() {
      this.$emit("toggle-mobile-nav");
    },
  },
};
</script>

<style scoped>
.top-card-dark {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #2e3348;
  color: #c1bfd6;
  padding: 7px 20px;
  border: 1px solid rgba(193, 191, 214, 0.2);
  border-radius: 8px;
  box-shadow: rgba(50, 50, 93, 0.2) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  font-family: "Rajdhani", sans-serif;
  margin-bottom: 15px;
}

.search-area {
  display: flex;
  align-items: center;
  flex-grow: 1;
  gap: 10px;
}

.search-area i {
  color: orange;
  font-size: 18px;
}

.search-area input {
  flex-grow: 1;
  border: none;
  outline: none;
  font-size: 16px;
  background: transparent;
  color: #c1bfd6;
  padding: 5px 0;
  font-family: "Asset", sans-serif;
}

.icon-area {
  display: flex;
  align-items: center;
  gap: 15px;
}

.icon-area i {
  font-size: 20px;
  color: #c1bfd6;
  cursor: pointer;
  transition: color 0.2s ease;
}

.notification-icon {
  position: relative;
}

.notification-dot {
  width: 8px;
  height: 8px;
  background: #ff4c51;
  border-radius: 50%;
  position: absolute;
  top: -2px;
  right: -2px;
}

.profile {
  position: relative;
  width: 38px;
  height: 38px;
  cursor: pointer;
}

.profile img {
  width: 100%;
  border-radius: 50%;
  height: 100%;
  object-fit: cover;
}

.online-indicator {
  width: 8px;
  height: 8px;
  background: #28c76f;
  border-radius: 50%;
  position: absolute;
  bottom: 0;
  right: 0;
  border: 2px solid #2e3348;
}

.fa-bars {
  display: none;
  font-size: 18px;
  cursor: pointer;
}

@media (max-width: 699px) {
  .top-card-dark {
    display: none;
  }
}
</style>
