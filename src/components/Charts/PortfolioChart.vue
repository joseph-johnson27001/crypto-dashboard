<template>
  <div class="chart-card">
    <h3 class="chart-title">{{ title }}</h3>
    <apexchart
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
          curve: "smooth",
          width: 2,
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
};
</script>

<style scoped>
.chart-card {
  background: #2e3348;
  border: 1px solid rgba(193, 191, 214, 0.2);
  border-radius: 8px;
  padding: 1.5rem;
  color: white;
  font-family: "Rajdhani", sans-serif;
}

.chart-title {
  font-size: 1rem;
  font-weight: 400;
  margin-top: 5px;
  margin-bottom: 5px;
  color: #c1bfd6;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}
</style>
