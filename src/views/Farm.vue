<template>
  <v-container>
    <chart-population :population="[1, 1, 2]" :years="[2, 3, 4,]" />
    <ChartTemperature/>
  </v-container>
</template>
<script>
import ChartPopulation from "../components/Farm/ChartPopulation.vue";
import ChartTemperature from "../components/Farm/ChartTemperature.vue";
export default {
  components: {
    ChartPopulation,
    ChartTemperature,
  },
  data: function () {
    return {
      chartOptions: {
        chart: {
          id: "chart-number",
        },
        xaxis: {
          categories: [
            2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020, 2021,
          ],
        },
      },
      series: [
        {
          name: "series-1",
          data: [30, 40, 35, 50, 49, 60, 70, 91, 85, 87, 121],
        },
      ],
    };
  },
};
</script>
