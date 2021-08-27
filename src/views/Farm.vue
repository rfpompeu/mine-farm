<template>
  <v-container>
    <chart-population
      :population="[5, 4, 2, 2, 3, 5, 6, 7, 12, 23]"
      :years="[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]"
    />
    <chart-temperature />
  </v-container>
</template>
<script>
import ChartPopulation from "../components/Farm/ChartPopulation.vue";
import ChartTemperature from "../components/Farm/ChartTemperature.vue";
import axios from 'axios'

export default {
  components: {
    ChartPopulation,
    ChartTemperature,
  },
  
  created() {
    this.getTemperatureApi();
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
  methods: {
    getTemperatureApi(){
      axios
      .get('')
      .then(response => (
        console.log(response)
      ))
    }
  },
};
</script>
