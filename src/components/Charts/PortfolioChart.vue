<template>
  <div class="chart-card">
    <div class="header-area">
      <h3 class="chart-title">
        <i class="header-icon fas fa-dollar-sign"></i>{{ title }}
      </h3>

      <select v-model="selectedTimeframe" @change="handleTimeframeChange">
        <option value="daily">Daily</option>
        <option value="weekly">Weekly</option>
        <option value="monthly">Monthly</option>
        <option value="yearly">Yearly</option>
      </select>
    </div>
    <apexchart
      ref="portfolioChart"
      type="area"
      height="300"
      :options="chartOptions"
      :series="series"
    />
  </div>
</template>

<script>
import ApexChart from "vue3-apexcharts";

export default {
  name: "PortfolioChart",
  components: {
    apexchart: ApexChart,
  },
  props: {
    title: String,
    series: Array,
    categories: Array,
  },
  data() {
    return {
      selectedTimeframe: "daily",
    };
  },
  computed: {
    chartOptions() {
      return {
        chart: {
          type: "area",
          toolbar: { show: false },
          zoom: { enabled: false },
        },
        colors: ["#FFA500"],
        dataLabels: { enabled: false },
        stroke: {
          curve: "straight",
          width: 3,
        },
        fill: {
          type: "gradient",
          gradient: {
            shadeIntensity: 1,
            opacityFrom: 0.3,
            opacityTo: 0,
            stops: [0, 90, 100],
          },
        },
        xaxis: {
          categories: this.categories,
          labels: {
            style: { colors: "#c1bfd6" },
          },
        },
        yaxis: {
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
  methods: {
    handleTimeframeChange() {
      this.$emit("update-chart", this.selectedTimeframe);
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
  overflow: hidden;
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

select {
  padding: 10px;
  background-color: #2e3348;
  color: #c1bfd6;
  border: 1px solid #3a4254;
  border-radius: 4px;
  font-size: 1rem;
  font-family: "Rajdhani", sans-serif;
  outline: none;
}
</style>
