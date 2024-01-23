<template>
  <div class="row">
    <h2>Vue Apex Chart Grouped Column Chart Example</h2>

    <div id="chart">
      <VueApexCharts type="bar" width="1500" height="1500" ref="userPerform" :options="chartOptions" :series="dynamicSeries"></VueApexCharts>
    </div>
  </div>
</template>

<script>
import VueApexCharts from "vue3-apexcharts";

export default {
  components: {
    VueApexCharts,
  },
  data() {
    return {
     
      categoryMap: [],
      dynamicSeries: [],
      chartOptions: {
        chart: {
          type: "bar",
          height: 700,
          stacked: true,
          toolbar: {
            show: false,
          },
        },
        stroke: {
          width: 0,
          colors: ["#fff"],
        },
        grid: {
          show: true,
          borderColor: "#ccc",
          strokeDashArray: 3,
        },
        dataLabels: {
          formatter: (val) => {
            return    (val / 1000) + "K";
          },
        },
        plotOptions: {
          bar: {
            horizontal: true,
            columnWidth: 100,
          },
        },
        xaxis: {
          type: "categories",
          categories: [
            "Sales Man 1",
            "Sales Man 2",
            "Sales Man 3",
            "Sales Man 4",
            "Sales Man 5",
          ],
        },
        fill: {
          opacity: 1,
        },
        colors: [
          "#4942E4",
          "#527853",
          "#11009E",
          "#65B741",
          "#80c7fd",
          "#008FFB",
          "#80f1cb",
          "#00E396",
        ],
        yaxis: {
          labels: {},
        },
        legend: {
          position: "top",
          horizontalAlign: "left",
        },
      },
    };
  },
  mounted() {
    this.generateDynamicSeries();
  },
  methods: {
    generateDynamicSeries() {
      const series = [
        { name: "Apple Target", group: "apple", data: [60040, 150040, 180040, 220040, 25000] },
        { name: "Samsung Target", group: "samsung", data: [100040, 200040, 120040, 180040, 22000] },
        { name: "Oneplus Target", group: "oneplus", data: [80040, 120040, 150040, 200040, 25000] },
        { name: "Apple Achieved", group: "apple", data: [120040, 180040, 220040, 250040, 28000] },
        { name: "Samsung Achieved", group: "samsung", data: [180040, 220040, 250040, 280040, 30000] },
        { name: "Oneplus Achieved", group: "oneplus", data: [160040, 200040, 220040, 250040, 28000] },
      ];
      this.dynamicSeries = series.map((s) => ({
        name: s.name,
        group: s.group,
        data: s.data,
      }));
    },
  },
};
</script>

<style scoped>
</style>
