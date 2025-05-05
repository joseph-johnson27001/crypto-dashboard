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
      <PortfolioChart
        title="Portfolio - $24,540"
        :series="portfolioSeries"
        :categories="portfolioCategories"
        @update-chart="updateChartData"
      />

      <!-- Recent Activity -->
      <div class="recent-activity-row">
        <RecentActivity :activities="recentActivities" />
      </div>

      <!-- Coin Table -->
      <CoinTable :coins="coinTableData" />

      <!-- Portfolio Allocation Chart -->
      <PortfolioAllocationChart
        title="Portfolio Allocation"
        :coins="coinAllocationData"
      />
    </div>
  </div>
</template>

<script>
import StatCard from "@/components/UI/StatCard.vue";
import PortfolioChart from "@/components/Charts/PortfolioChart.vue";
import CoinTable from "@/components/Tables/CoinTable.vue";
import RecentActivity from "@/components/Activity/RecentActivity.vue";
import PortfolioAllocationChart from "@/components/Charts/PortfolioAllocationChart.vue";

export default {
  name: "DashboardPage",
  components: {
    StatCard,
    PortfolioChart,
    CoinTable,
    RecentActivity,
    PortfolioAllocationChart,
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
      coinAllocationData: [
        { name: "Bitcoin", percentage: 60 },
        { name: "Ethereum", percentage: 25 },
        { name: "Solana", percentage: 10 },
        { name: "Cardano", percentage: 5 },
      ],
      recentActivities: [
        {
          type: "purchase",
          text: "Purchased 1.5 BTC",
          time: "2 hours ago",
        },
        {
          type: "sell",
          text: "Sold 10 ETH",
          time: "1 day ago",
        },
        {
          type: "alert",
          text: "Price drop alert for Solana",
          time: "3 hours ago",
        },
        {
          type: "rebalance",
          text: "Rebalanced portfolio",
          time: "Yesterday",
        },
        {
          type: "deposit",
          text: "Deposited $5000",
          time: "1 week ago",
        },
        {
          type: "purchase",
          text: "Purchased 500 ADA",
          time: "1 week ago",
        },
        {
          type: "sell",
          text: "Sold 20 SOL",
          time: "2 weeks ago",
        },
      ],
      portfolioSeries: [
        {
          name: "Portfolio Value",
          data: [23000, 23500, 22800, 24200, 24540, 24300, 24540],
        },
      ],
      portfolioCategories: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
      portfolioData: {
        daily: {
          series: [
            {
              name: "Portfolio Value",
              data: [23000, 23500, 22800, 24200, 24540, 24300, 24540],
            },
          ],
          categories: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        weekly: {
          series: [
            {
              name: "Portfolio Value",
              data: [23000, 24000, 25000, 24500, 25500, 26000, 26500],
            },
          ],
          categories: [
            "Week 1",
            "Week 2",
            "Week 3",
            "Week 4",
            "Week 5",
            "Week 6",
            "Week 7",
          ],
        },
        monthly: {
          series: [
            {
              name: "Portfolio Value",
              data: [
                23000, 24500, 27000, 28000, 30000, 32000, 35000, 36000, 37000,
                38000, 39000, 40000,
              ],
            },
          ],
          categories: [
            "Jan",
            "Feb",
            "Mar",
            "Apr",
            "May",
            "Jun",
            "Jul",
            "Aug",
            "Sep",
            "Oct",
            "Nov",
            "Dec",
          ],
        },
        yearly: {
          series: [
            {
              name: "Portfolio Value",
              data: [12000, 20000, 21000, 24000, 36000],
            },
          ],
          categories: ["2020", "2021", "2022", "2023", "2024"],
        },
      },
      selectedTimeframe: "daily",
      coinTableData: [
        {
          name: "Bitcoin",
          symbol: "BTC",
          price: "$64,200",
          holdings: "0.25",
          value: "$16,050",
          change24h: "+2.1%",
          change7d: "+8.3%",
          icon: "https://assets.coingecko.com/coins/images/1/large/bitcoin.png",
        },
        {
          name: "Ethereum",
          symbol: "ETH",
          price: "$3,120",
          holdings: "1.5",
          value: "$4,680",
          change24h: "-0.6%",
          change7d: "+2.9%",
          icon: "https://assets.coingecko.com/coins/images/279/large/ethereum.png",
        },
        {
          name: "Solana",
          symbol: "SOL",
          price: "$140",
          holdings: "10",
          value: "$1,400",
          change24h: "+5.2%",
          change7d: "+12.0%",
          icon: "https://assets.coingecko.com/coins/images/4128/large/solana.png",
        },
        {
          name: "Cardano",
          symbol: "ADA",
          price: "$0.45",
          holdings: "2000",
          value: "$900",
          change24h: "+1.3%",
          change7d: "+4.7%",
          icon: "https://assets.coingecko.com/coins/images/975/large/cardano.png",
        },
        {
          name: "Ripple",
          symbol: "XRP",
          price: "$0.52",
          holdings: "1500",
          value: "$780",
          change24h: "-0.8%",
          change7d: "+1.5%",
          icon: "https://assets.coingecko.com/coins/images/44/large/xrp-symbol-white-128.png",
        },
      ],
    };
  },
  methods: {
    updateChartData(newTimeframe) {
      this.selectedTimeframe = newTimeframe;
      const { series, categories } = this.portfolioData[this.selectedTimeframe];
      this.portfolioSeries = series;
      this.portfolioCategories = categories;
    },
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
  margin-top: 15px;
  gap: 15px;
}

@media (max-width: 1700px) {
  .kpi-row {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 1000px) {
  .chart-row {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 800px) {
  .kpi-row {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 500px) {
  .kpi-row {
    grid-template-columns: 1fr;
  }
}
</style>
