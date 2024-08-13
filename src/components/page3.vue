<template>
    <div class="box">
        <h4>
            库存统计
        </h4>
        <div class="echarts" ref="contrainer">

        </div>
    </div>
</template>

<script setup>
import { ref,onMounted } from 'vue'
import * as echarts from 'echarts'


let contrainer = ref()

let option = {
  legend: {
    left: 'center',
    top: 'bottom',
    data: [
      '热食',
      '服饰',
      '数码',
      '家电',
      '家居',
      '日化'
    ]
  },
  series: [
    {
      name: 'Area Mode',
      type: 'pie',
      radius: [30, 80],
      center: ['50%', '40%'],
      roseType: 'area',
      itemStyle: {
        borderRadius: 5
      },
      data: [
        { value: 30, name: '热食' },
        { value: 28, name: '服饰' },
        { value: 26, name: '数码' },
        { value: 24, name: '家电' },
        { value: 22, name: '家居' },
        { value: 20, name: '日化' },
      ]
    }
  ]
};

onMounted(() =>{
    let myCharts = echarts.init(contrainer.value);
    myCharts.setOption(option)
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