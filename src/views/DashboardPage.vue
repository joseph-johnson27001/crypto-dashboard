<template>
  <div class="dashboard">
    <div class="kpi-row">
      <StatCard
        v-for="(card, index) in statCards"
        :key="index"
        :label="card.label"
        :value="card.value"
        :change="card.change"
      >
        <template #icon>
          <i :class="card.icon"></i>
        </template>
      </StatCard>
    </div>
  </div>
</template>

<script>
import StatCard from "@/components/UI/StatCard.vue";

export default {
  name: "DashboardPage",
  components: {
    StatCard,
  },
  data() {
    return {
      statCards: [
        {
          label: "Portfolio Value",
          value: "$24,540",
          change: "+2.6%",
          icon: "fas fa-wallet",
        },
        {
          label: "24h Change",
          value: "+$620",
          change: "+2.6%",
          icon: "fas fa-arrow-trend-up",
        },
        {
          label: "BTC Price",
          value: "$64,200",
          change: "-0.8%",
          icon: "fab fa-bitcoin",
        },
        {
          label: "ETH Price",
          value: "$3,120",
          change: "+1.3%",
          icon: "fab fa-ethereum",
        },
      ],
    };
  },
};
</script>

<style scoped>
.dashboard {
  padding: 2rem;
  color: white;
}

.kpi-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 15px;
}
</style>
