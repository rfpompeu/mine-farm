<template>
  <v-container>
    <chart-population
      :population="[5, 4, 2, 2, 3, 5, 6, 7, 12, 23, 34, 32]"
      :years="[
        2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020, 2021,
      ]"
    />
    <chart-temperature />
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

  created() {},
  data() {
    return {};
  },
  methods: {},
};
</script>
