<template>
  <div :style="canvasStyle" ref="canvas"></div>
</template>

<script>
import echarts from '../echarts-base'
import 'echarts/lib/chart/bar'
import { bar } from './bar'
import chartMixin from '../mixins'
export default {
  name: 'VeBar',
  mixins: [chartMixin],
  created () {
    this.chartHandler = bar
    this.echartsLib = echarts
  }
}
</script>
