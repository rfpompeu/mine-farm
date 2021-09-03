<template>
  <v-container>
    <v-row class="text-h4 my-5">População</v-row>
    <apexchart
      height="350"
      type="bar"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </v-container>
</template>
<script>
export default {
  name: "ChartPopulation",
  props: {
    years: Array,
    population: Array,
  },
  data() {
    return {
      chartOptions: {
        chart: {
          id: "chart-number",
        },
        xaxis: {
          categories: this.years,
        },
      },
      series: [
        {
          name: "animais",
          data: this.population,
        },
      ],
    };
  },
};
</script>
