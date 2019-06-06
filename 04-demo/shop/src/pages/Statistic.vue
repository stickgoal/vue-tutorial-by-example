<template>
<div id="main">
  <el-container>
    <el-main>
      <el-row type="flex" class="row-bg">
      <el-col :span="8" :offset="8">
        <div ref="myEchart" style="width:500px; height:500px"></div>
      </el-col>
      </el-row>
    </el-main>
  </el-container>
</div>
</template>

<script>
import echarts from 'echarts'
import axios from 'axios'

export default {
  name: 'Statistic',
  data () {
    return {
      barChartData: []
    }
  },
  methods: {
    initChart () {
      this.chart = echarts.init(this.$refs.myEchart)
      // 把配置和数据放这里
      var data = this.barChartData
      this.chart.setOption({
        color: ['#3398DB'],
        tooltip: {
          trigger: 'axis',
          axisPointer: { // 坐标轴指示器，坐标轴触发有效
            type: 'shadow' // 默认为直线，可选为：'line' | 'shadow'
          }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [{
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
          axisTick: {
            alignWithLabel: true
          }
        }],
        yAxis: [{
          type: 'value'
        }],
        series: [{
          name: '直接访问',
          type: 'bar',
          barWidth: '60%',
          data: data
        }]
      })
    }
  },
  mounted () {
    this.barChartData = [10, 100, 30, 20, 120, 20, 70]

    this.initChart()
    // 从后台获取标签
    // axios.get('http://localhost:8088/getTags').then(response => {
    //   if (response.data.success) {
    //     this.paymentTags = response.data.paymentTags
    //     this.gainTags = response.data.gainTags
    //     this.currentTags = this.paymentTags
    //     this.form.category = this.currentTags[0]
    //   }
    // })
  }
}
</script>

<style scoped>

</style>
