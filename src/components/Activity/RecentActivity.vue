<template>
  <div class="recent-activity">
    <h3 class="activity-title">
      <i class="header-icon fas fa-exchange-alt"></i> Recent Activity
    </h3>
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
    activities: Array,
  },
  methods: {
    getIconClass(type) {
      switch (type) {
        case "purchase":
          return "fas fa-shopping-cart";
        case "sell":
          return "fas fa-wallet";
        case "alert":
          return "fas fa-bell";
        case "deposit":
          return "fas fa-plus-circle";
        case "rebalance":
          return "fas fa-sync-alt";
        default:
          return "fas fa-question";
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

.header-icon {
  color: orange;
  font-size: 1.2rem;
  margin-right: 5px;
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
  font-size: 1rem;
  margin-right: 0.7rem;
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

@media (max-width: 350px) {
  .activity-item {
    flex-direction: column;
    align-items: flex-start;
  }

  .activity-text,
  .activity-time {
    flex: 1 1 100%;
    text-align: left;
    font-size: 0.9rem;
  }

  .activity-time {
    font-size: 0.8rem;
    margin-top: 4px;
  }

  .activity-icon {
    margin-bottom: 4px;
  }
}
</style>
