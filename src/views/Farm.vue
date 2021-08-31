<template>
  <v-container>
    <chart-population
      :population="[5, 4, 2, 2, 3, 5, 6, 7, 12, 23]"
      :years="[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]"
    />
    <chart-temperature
      :temperatures="temperatureInLocu"
      :temperaturesInBarn="temperatureInBarn"
    />
  </v-container>
</template>
<script>
import ChartPopulation from "../components/Farm/ChartPopulation.vue";
import ChartTemperature from "../components/Farm/ChartTemperature.vue";
import axios from "axios";

export default {
  components: {
    ChartPopulation,
    ChartTemperature,
  },

  created() {
    this.getTemperatureApi("Belém-Pa");
  },
  data: function () {
    return {
      geoCode: {
        "Belém-Pa": 1501402,
      },
      temperatureInLocu: [],
      temperatureInBarn: [],
      temperatures: [],
    };
  },
  methods: {
    getTimeByDate(date) {
      let day = date.split("/")[0],
        month = date.split("/")[1],
        year = date.split("/")[2];
      return new Date(year, month, day).getTime();
    },
    getTemperatureApi(city) {
      axios
        .get("https://apiprevmet3.inmet.gov.br/previsao/" + this.geoCode[city])
        .then(({ data }) => {
          this.dates = Object.keys(data[this.geoCode[city]]);
          this.dates.forEach((element) => {
            if ("tarde" in data[this.geoCode[city]][element]) {
              let dayTemperature = data[this.geoCode[city]][element]["tarde"];
              let temperature =
                (dayTemperature["temp_max"] + dayTemperature["temp_min"]) / 2;
              this.temperatures.push(temperature);
            } else {
              let dayTemperature = data[this.geoCode[city]][element];
              let temperature =
                (dayTemperature["temp_max"] + dayTemperature["temp_min"]) / 2;
              this.temperatures.push(temperature);
            }
          });
          this.temperatureInLocu = this.temperatures.map((element, index) => {
            return [this.getTimeByDate(this.dates[index]), element];
          });
          this.temperatureInBarn = this.temperatures.map((element, index) => {
            return [this.getTimeByDate(this.dates[index]), element + 3];
          });
          console.log(this.temperatureInBarn);
        });
    },
  },
};
</script>
