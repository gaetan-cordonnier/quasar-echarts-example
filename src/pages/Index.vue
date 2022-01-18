<template>
  <q-page class="">
    <div class="row q-col-gutter-sm q-ml-xs q-mr-sm q-py-sm">
      <div class="col-lg-10 col-md-6 col-sm-12 col-xs-12">
      <q-btn @click="updateFunction" color="secondary" class="float-right" rounded>Update Bar- Chart</q-btn>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <line-chart></line-chart>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <bar-chart :data="updatingData"></bar-chart>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <pie-chart></pie-chart>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <scatter-chart></scatter-chart>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <dotted-bar-chart></dotted-bar-chart>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <guage-chart></guage-chart>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <boxplot></boxplot>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <area-chart></area-chart>
      </div>
    </div>
  </q-page>
</template>

<script>
import LineChart from "components/LineChart";
import BarChart from "components/BarChart";
import PieChart from "components/PieChart";
import ScatterChart from "components/ScatterChart";
import DottedBarChart from "components/DottedBarChart";
import GuageChart from "components/GuageChart";
import Boxplot from "components/BoxChart";
import AreaChart from "components/AreaChart";

export default {
  name: 'PageIndex',
  components: {AreaChart, Boxplot, GuageChart, DottedBarChart, ScatterChart, PieChart, BarChart, LineChart},

  data () {
    return {
      updatingData: [
        ['product', '2015', '2016', '2017'],
        ['Matcha Latte', 43.3, 85.8, 93.7],
        ['Milk Tea', 83.1, 73.4, 55.1],
        ['Cheese Cocoa', 86.4, 65.2, 82.5],
        ['Walnut Brownie', 72.4, 53.9, 39.1]
      ]
    }
  },

  methods: {
    updateFunction () {
      this.updatingData = [
        ['product', '2018', '2019', '2020'],
        ['Matcha Latte', 53.3, 25.8, 73.7],
        ['Milk Tea', 33.1, 43.4, 85.1],
        ['Cheese Cocoa', 26.4, 15.2, 32.5],
        ['Walnut Brownie', 42.4, 33.9, 89.1]
      ]
    }
  }
}
</script>
