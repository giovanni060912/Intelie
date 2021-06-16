
<script>
import { Line } from "vue-chartjs";

export default {
  extends: Line,
  data: () => ({
    chartdata: {
      labels: ["minResponseTime", "maxResponseTime"],
      datasets: [],
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
    },
  }),

created() {
const data  = JSON.parse(localStorage.getItem('DataListChart')) || []
this.chartdata.datasets = data


},
  mounted() {
    this.renderChart(this.chartdata, this.options);
  },
};
</script>

<style>
</style>