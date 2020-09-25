<template>
  <div class="section">
    <h2>{{ title }}</h2>
    <div :id="id" style="width: 100%; height: 800px;"></div>
  </div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";

export default {
  name: 'Lines',
  props: {
    id: { type: String, default: '' },
    title: { type: String, default: '' },
    data: { type: Array, default: () => []}
  },
  mounted() {
    am4core.ready(() => {
      // Themes begin
      am4core.useTheme(am4themes_animated);
      // Themes end

      var chart = am4core.create(this.id, am4charts.XYChart);

      chart.data = this.data;

      // Create axes
      const dateAxis = chart.xAxes.push(new am4charts.DateAxis());
      dateAxis.renderer.minGridDistance = 50;

      /* eslint-disable-next-line */
      var valueAxis = chart.yAxes.push(new am4charts.ValueAxis());

      // Create series
      var series1 = chart.series.push(new am4charts.LineSeries());
      series1.dataFields.valueY = "value";
      series1.dataFields.dateX = "date";
      series1.tooltipText = "{value}"
      series1.tensionX = 0.9;
      series1.strokeWidth = 5;
      series1.tooltip.pointerOrientation = "vertical";

      chart.cursor = new am4charts.XYCursor();
      chart.cursor.snapToSeries = series1;
      chart.cursor.xAxis = dateAxis;

      //chart.scrollbarY = new am4core.Scrollbar();
      // chart.scrollbarX = new am4core.Scrollbar();

      }); // end am4core.ready()
  }
}
</script>

<style>

</style>