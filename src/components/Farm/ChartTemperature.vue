<template>
  <v-container>
    <v-row class="text-h4 my-5">Temoeraturas</v-row>
    <apexchart
      type="area"
      height="350"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </v-container>
</template>
<script>
export default {
  name: "ChartTemperatures",
  props: {
    years: Array,
    temperatures: Array,
  },
  methods: {
    generateDayWiseTimeSeries(baseval, count, yrange) {
      var i = 0;
      var series = [];
      while (i < count) {
        var x = baseval;
        var y =
          Math.floor(Math.random() * (yrange.max - yrange.min + 1)) +
          yrange.min;

        series.push([x, y]);
        baseval += 86400000;
        i++;
      }
      return series;
    },
  },

  data() {
    return {
      series: [
        {
          name: "Temoeratura",
          data: this.generateDayWiseTimeSeries(
            new Date("11 Feb 2021 GMT").getTime(),
            20,
            {
              min: 10,
              max: 39,
            }
          ),
        },
        {
          name: "Temperatura no Celeiro",
          data: this.generateDayWiseTimeSeries(
            new Date("11 Feb 2021 GMT").getTime(),
            20,
            {
              min: 10,
              max: 45,
            }
          ),
        },
      ],
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
};
</script>
