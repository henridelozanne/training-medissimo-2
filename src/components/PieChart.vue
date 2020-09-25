<template>
  <div class="section">
    <h1>{{ title }}</h1>
    <div :id="id" style="width: 100%; height: 800px;"></div>
    <h3 v-if="emptyCenter" class="total-displayed">{{ totalDisplayed }}</h3>
    <p v-if="bottomInfo" class="bottom-info">{{ bottomInfo }}</p>
  </div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";

export default {
  name: 'PieChart',
  props: {
    title: { type: String, default: '' },
    data: { type: Array, default: () => [] },
    id: { type: String, default: '' },
    emptyCenter: { type: Boolean, default: false },
    bottomInfo: { type: String, default: '' }
  },
  computed: {
    totalDisplayed() {
      const values = [];
      this.data.forEach((item) => {
        values.push(item.value);
      })
      return values.reduce((a, b) => a + b, 0);
    }
  },
  mounted() {
    am4core.ready(() => {
      // Themes begin
      am4core.useTheme(am4themes_animated);

      let chart = am4core.create(this.id, am4charts.PieChart);
      // Create pie series
      let series = chart.series.push(new am4charts.PieSeries());
      series.dataFields.value = "value";
      series.dataFields.category = "category";

      // Center hole
      if (this.emptyCenter) {
        chart.innerRadius = am4core.percent(50);
      }

      // Add data
      chart.data = this.data;

      // And, for a good measure, let's add a legend
      // chart.legend = new am4charts.Legend();

      // This creates initial animation
      chart.hiddenState.properties.opacity = 1;
      // chart.hiddenState.properties.endAngle = -90;
      // chart.hiddenState.properties.startAngle = -90;
    });
  }
}
</script>

<style>
.total-displayed {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%);
  font-size: 2em;
  margin: 0;
}

.bottom-info {
  font-size: 1.2em;
}
</style>