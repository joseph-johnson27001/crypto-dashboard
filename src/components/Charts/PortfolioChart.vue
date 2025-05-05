<template>
  <div class="chart-card">
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
  data() {
    return {
      series: [
        {
          name: "Portfolio Value",
          data: [23000, 23500, 22800, 24200, 24540, 24300, 24800],
        },
      ],
      chartOptions: {
        chart: {
          type: "area",
          toolbar: {
            show: false,
          },
          zoom: {
            enabled: false,
          },
        },
        colors: ["#FFA500"],
        dataLabels: {
          enabled: false,
        },
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
          categories: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
          labels: {
            style: {
              colors: "#c1bfd6",
            },
          },
        },
        yaxis: {
          labels: {
            style: {
              colors: "#c1bfd6",
            },
          },
        },
        tooltip: {
          theme: "dark",
        },
        grid: {
          borderColor: "rgba(193, 191, 214, 0.2)",
        },
      },
    };
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
</style>
