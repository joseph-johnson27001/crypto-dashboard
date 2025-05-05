<template>
  <div class="dashboard">
    <!-- KPI Cards -->
    <div class="kpi-row">
      <StatCard
        v-for="(card, index) in statCards"
        :key="index"
        :label="card.label"
        :value="card.value"
        :change="card.change"
        :icon="card.icon"
      />
    </div>

    <!-- Portfolio Chart -->
    <div class="chart-row">
      <PortfolioChart />
    </div>
  </div>
</template>

<script>
import StatCard from "@/components/UI/StatCard.vue";
import PortfolioChart from "@/components/Charts/PortfolioChart.vue";

export default {
  name: "DashboardPage",
  components: {
    StatCard,
    PortfolioChart,
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
        {
          label: "Top Gainer",
          value: "SOL +8.2%",
          change: "+8.2%",
          icon: "fas fa-fire",
        },
        {
          label: "Top Loser",
          value: "DOGE -3.7%",
          change: "-3.7%",
          icon: "fas fa-sad-tear",
        },
      ],
    };
  },
};
</script>

<style scoped>
.kpi-row {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 15px;
}

.chart-row {
  display: grid;
  grid-template-columns: 2fr 1fr;
  margin-top: 20px;
}
</style>
