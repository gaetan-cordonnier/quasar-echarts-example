<template>
  <div>
    <q-card>
      <q-card-section class="text-h6">
        Bar Chart
        <q-btn icon="fa fa-download" class="float-right" @click="SaveImage" flat dense>
          <q-tooltip>Download PNG</q-tooltip>
        </q-btn>
      </q-card-section>
      <q-card-section>
        <div ref="barchart" id="barChart" style="height: 250px;"></div>
      </q-card-section>
      <q-resize-observer @resize="onResize"/>
    </q-card>
  </div>
</template>

<script>
export default {
  name: "BarChart",

  props: {
    data: {
      type: Array,
      default: []
    }
  },

  data(props) {
    return {
      model: false,
      options: {
        legend: {
          bottom: 10,
        },
        tooltip: {},
        dataset: {
          source: props.data
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '20%',
          top: '5%',
          containLabel: true
        },
        xAxis: {type: 'category'},
        yAxis: {},
        // Declare several bar series, each will be mapped
        // to a column of dataset.source by default.
        series: [
          {type: 'bar'},
          {type: 'bar'},
          {type: 'bar'}
        ]
      },
      bar_chart: null
    }
  },
  mounted() {
    this.init();
  },
  watch: {
    '$q.dark.isActive': function () {
      this.init();
    }
  },
  methods: {

    SaveImage() {
      const linkSource = this.bar_chart.getDataURL();
      const downloadLink = document.createElement('a');
      document.body.appendChild(downloadLink);

      downloadLink.href = linkSource;
      downloadLink.target = '_self';
      downloadLink.download = 'BarChart.png';
      downloadLink.click();
    },
    init() {
      let barChart = document.getElementById('barChart');
      echarts.dispose(barChart);
      let theme = this.model ? 'dark' : 'light';
      this.bar_chart = echarts.init(barChart, theme);
      this.bar_chart.setOption(this.options)
    },
    onResize() {
      if (this.bar_chart) {
        this.bar_chart.resize();
      }
    }
  }
}
</script>

<style scoped>

</style>
