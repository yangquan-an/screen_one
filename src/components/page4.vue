<template>
    <div class="box">
        <h4>
            产品类别
        </h4>
        <div class="echarts" ref="contrainer">

        </div>
    </div>
</template>

<script setup>

import { ref,onMounted } from 'vue'
import * as echarts from 'echarts'
const rawData = [
  [100, 302, 301, 334, 390, 330, 320],
  [320, 132, 101, 134, 90, 230, 210],
  [220, 182, 191, 234, 290, 330, 310],
  [150, 212, 201, 154, 190, 330, 410],
  [820, 832, 901, 934, 1290, 1330, 1320]
];
const totalData = [];
for (let i = 0; i < rawData[0].length; ++i) {
  let sum = 0;
  for (let j = 0; j < rawData.length; ++j) {
    sum += rawData[j][i];
  }
  totalData.push(sum);
}
console.log(totalData)
const grid = {
  left: 40,
  right: 10,
  top: 50,
  bottom: 20
};
const series = [
  '服饰',
  '数码',
  '家电',
  '家居',
  '日化'
].map((name, sid) => {
  return {
    name,
    type: 'bar',
    stack: 'total',
    barWidth: '60%',
    label: {
      show: true,
      color:"white",
      formatter: (params) => Math.round(params.value)
    },
    data: rawData[sid].map((d, did) =>
      totalData[did] <= 0 ? 0 : d
    )
  };
});
let option = {
  legend: {
    selectedMode: false
  },
  grid,
  yAxis: {
    axisLabel:{
        color:"white"
    },
    type:'value',
    min: 0,
    max: 1600,
    interval: 200,
  },
  xAxis: {
    axisLabel:{
        color:"white"
    },
    type: 'category',
    data: ['周一', '周二', '周三', '周四', '周五', '周六', '周天']
  },
  series
};

let contrainer = ref()

onMounted(() =>{
   let myEcharts = echarts.init(contrainer.value)
   myEcharts.setOption(option)
})

</script>


<style scoped>
.box{
    height: 5rem;
    border: 1px solid blue;
    margin: .25rem;
    background: rgb(40, 137, 234,0.6);
    text-align: center;
    font-size: .4rem;
    color: white;
}
.echarts{
    width: 100%;
    height: 4rem;
}
</style>