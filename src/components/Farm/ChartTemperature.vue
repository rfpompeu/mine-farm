<template>
  <v-container>
    Clima: {{this.weather}}
    <v-row class="text-h4 my-5">Temperatura</v-row>
    <apexchart
      height="350"
      :options="chartOptions"
      :series="[
        {
          name: 'Local',
          data: temperatureInTime,
        },
        {
          name: 'Celeiro',
          data: temperatureInTime.map((element) => {
            return [element[0], Math.floor(Math.random() * 7)];
          }),
        },
      ]"
    ></apexchart>
  </v-container>
</template>
<script>
import axios from "axios";
export default {
  name: "ChartTemperatures",
  created() {
    this.getDataApi(this.geoCode["Belém-Pa"]);
  },
  data() {
    return {
      geoCode: {
        "Belém-Pa": 1501402,
      },
      temperatureInTime: [],
      weather: null,
      chartOptions: {
        chart: {
          type: "area",
          height: 350,
          stacked: true,
          events: {
            selection: function (chart, e) {
              console.log(new Date(e.xaxis.min));
            },
          },
        },
        colors: ["#008FFB", "#00E396", "#CED4DC"],
        dataLabels: {
          enabled: false,
        },
        stroke: {
          curve: "smooth",
        },
        fill: {
          type: "gradient",
          gradient: {
            opacityFrom: 0.6,
            opacityTo: 0.8,
          },
        },
        legend: {
          position: "top",
          horizontalAlign: "left",
        },
        xaxis: {
          type: "datetime",
        },
      },
    };
  },
  methods: {
    generateDayWiseTimeSeries(baseval, count, yrange) {
      var i = 0;
      var series = [];
      while (i < count) {
        var y =
          Math.floor(Math.random() * (yrange.max - yrange.min + 1)) +
          yrange.min;

        series.push([baseval, y]);
        baseval += 86400000;
        i++;
      }
      console.log(series);
      return series;
    },
    getDataApi(city) {
      axios
        .get("https://apiprevmet3.inmet.gov.br/previsao/" + city)
        .then(({ data }) => {
          var temperature = 0;
          let days = Object.keys(data[city]);
          this.temperatureInTime = days.map((element) => {
            if ("manha" in data[city][element]) {
              temperature =
                (data[city][element]["manha"]["temp_max"] +
                  data[city][element]["manha"]["temp_min"]) /
                2;
              if (!this.weather) {
                this.weather = data[city][element]["manha"]["resumo"];
                console.log(data[city][element]["manha"]["resumo"]);
              }
            } else {
              temperature =
                (data[city][element]["temp_max"] +
                  data[city][element]["temp_min"]) /
                2;
            }
            if (!temperature) {
              temperature = 32;
            }
            let dateArray = element.split("/");
            let time = new Date(
              dateArray[2],
              dateArray[1] - 1,
              dateArray[0]
            ).getTime();
            return [time, temperature];
          });
        });
    },
  },
};
</script>
