<template>
  <div class="stat-card">
    <div class="stat-header">
      <i :class="['stat-icon', icon]"></i>
      <span class="label">{{ label }}</span>
    </div>
    <div class="stat-value">{{ value }}</div>
    <div
      v-if="change"
      class="stat-change"
      :class="{ positive: isPositive, negative: !isPositive }"
    >
      <i :class="isPositive ? 'fas fa-arrow-up' : 'fas fa-arrow-down'"></i>
      {{ change }}
    </div>
  </div>
</template>

<script>
export default {
  name: "StatCard",
  props: {
    label: String,
    value: String,
    change: String,
    icon: String,
  },
  computed: {
    isPositive() {
      return this.change && !this.change.startsWith("-");
    },
  },
};
</script>

<style scoped>
.stat-card {
  background: #2e3348;
  border: 2px solid rgba(193, 191, 214, 0.2);
  border-radius: 8px;
  padding: 1.2rem;
  min-width: 180px;
  color: #c1bfd6;
  font-family: "Rajdhani", sans-serif;
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  transition: border 0.1s linear;
  cursor: pointer;
}

.stat-header {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.95rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.stat-icon {
  color: orange;
  font-size: 1rem;
}

.stat-value {
  font-size: 1.8rem;
  font-weight: 600;
  color: white;
}

.stat-change {
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 6px;
}

.stat-change i {
  font-size: 0.85rem;
}

.stat-change.positive {
  color: #4caf50;
}

.stat-change.negative {
  color: #f44336;
}
</style>
