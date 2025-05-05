<template>
  <div class="recent-activity">
    <h3 class="activity-title">Recent Activity</h3>
    <div class="activity-list">
      <div
        v-for="(activity, index) in activities"
        :key="index"
        class="activity-item"
      >
        <span :class="getIconClass(activity.type)" class="activity-icon"></span>
        <span class="activity-text">{{ activity.text }}</span>
        <span class="activity-time">{{ activity.time }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecentActivity",
  props: {
    activities: Array, // Receiving activities as prop from DashboardPage
  },
  methods: {
    getIconClass(type) {
      switch (type) {
        case "purchase":
          return "fas fa-shopping-cart"; // Shopping cart for purchase
        case "sell":
          return "fas fa-wallet"; // Wallet icon for sale
        case "alert":
          return "fas fa-bell"; // Bell icon for alerts
        case "deposit":
          return "fas fa-plus-circle"; // Plus circle for deposits
        case "rebalance":
          return "fas fa-sync-alt"; // Sync for portfolio rebalance
        default:
          return "fas fa-question"; // Default fallback
      }
    },
  },
};
</script>

<style scoped>
.recent-activity {
  background: #2e3348;
  padding: 1rem;
  border-radius: 8px;
  border: 1px solid rgba(193, 191, 214, 0.2);
  color: #c1bfd6;
  font-family: "Rajdhani", sans-serif;
}

.activity-title {
  font-size: 1.1rem;
  text-transform: uppercase;
  margin-top: 10px;
  color: white;
}

.activity-item {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
  padding: 0.5rem;
  border-bottom: 1px solid #3a4254;
}

.activity-item:hover {
  background: rgba(255, 255, 255, 0.05);
  cursor: pointer;
}

.activity-icon {
  font-size: 1.2rem;
  margin-right: 0.5rem;
  color: orange;
}

.activity-text {
  flex: 1;
  color: #c1bfd6;
}

.activity-time {
  font-size: 0.85rem;
  color: #a9a6c1;
}
</style>
