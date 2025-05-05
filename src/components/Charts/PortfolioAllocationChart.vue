<template>
  <div class="chart-card">
    <div class="header-area">
      <h3 class="chart-title">
        <i class="header-icon fas fa-bar-chart"></i>{{ title }}
      </h3>
    </div>
    <apexchart
      type="bar"
      height="250"
      :options="chartOptions"
      :series="series"
    />
  </div>
</template>

<script>
import ApexChart from "vue3-apexcharts";

export default {
  name: "PortfolioAllocationChart",
  components: {
    apexchart: ApexChart,
  },
  props: {
    title: String,
    coins: Array,
  },
  data() {
    return {
      series: [
        {
          name: "Allocation",
          data: [],
        },
      ],
    };
  },
  computed: {
    chartOptions() {
      return {
        chart: {
          type: "bar",
          toolbar: { show: false },
          zoom: { enabled: false },
        },
        plotOptions: {
          bar: {
            columnWidth: "60%",
          },
        },
        colors: ["#FFA500", "#8e44ad", "#3498db", "#e74c3c"],
        dataLabels: { enabled: false },
        stroke: {
          width: 2,
        },
        xaxis: {
          categories: this.coins.map((coin) => coin.name),
          labels: {
            style: { colors: "#c1bfd6" },
          },
        },
        yaxis: {
          title: {
            text: "Percentage",
            style: {
              color: "#c1bfd6",
            },
          },
          labels: {
            style: { colors: "#c1bfd6" },
          },
        },
        tooltip: {
          theme: "dark",
        },
        grid: {
          borderColor: "rgba(193, 191, 214, 0.2)",
        },
      };
    },
  },
  watch: {
    coins: {
      handler(newCoins) {
        this.series[0].data = newCoins.map((coin) => coin.percentage);
      },
      immediate: true,
    },
  },
};
</script>

<style scoped>
.chart-card {
  background: #2e3348;
  border: 1px solid rgba(193, 191, 214, 0.2);
  border-radius: 8px;
  padding: 1rem;
  color: white;
  font-family: "Rajdhani", sans-serif;
}

.header-area {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.chart-title {
  margin-top: 5px;
  margin-bottom: 0px;
  font-size: 1.1rem;
  text-transform: uppercase;
  color: white;
}

.header-icon {
  color: orange;
  font-size: 1.2rem;
  margin-right: 5px;
}
</style>
