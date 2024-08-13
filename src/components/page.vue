<template>
    <div class="box">
        <h4>销售总量</h4>
        <div class="echarts" ref="echartsBox">

        </div>
    </div>
</template>

<script setup>
import { onMounted,ref } from 'vue';
import * as echarts from 'echarts';

// 声明 ref 变量
let echartsBox = ref()


let option = {
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    }
  },
  legend: {},
  grid: {
    left: '1%',
    right: '8%',
    top:'9%',
    containLabel: true
  },
  xAxis: {
    type: 'value',
    boundaryGap: [0,0.1],
    axisLabel:{
        color:'white'
    }
  },
  yAxis: {
    type: 'category',
    data: [
      {
        value:'洗碗机',
        textStyle:{
          color:'white'
        }
      },
      {
        value:'空调',
        textStyle:{
          color:'white'
        }
      }, {
        value:'烤箱',
        textStyle:{
          color:'white'
        }
      }, {
        value:'电视机',
        textStyle:{
          color:'white'
        }
      }, {
        value:'冰箱',
        textStyle:{
          color:'white'
        }
      }],
    axisLabel:{
      fontSize:15
    }
  },
 
  series: [
    {
      type: 'bar',
      data: [300, 500, 1000, 1500, 2000, 2500],
      label:{
        show:true,
        position:'right',
        fontSize:15,
        color:'white'
      }
    }
  ]
};

option.series[0].data.forEach((item,index) =>{
  option.series[0].data[index] = {
    value:item,
    itemStyle:{
      borderRadius:[0,20,20,0],
      color:new echarts.graphic.LinearGradient(0, 0, 1, 0, [
            { offset: 0, color: '#336a9f' },
            { offset: 0.7, color: '#5ca09b' },
            { offset: 1, color: '#95a761' }
        ])
    }
  } 
})

onMounted(() =>{
    var myCharts  =   echarts.init(echartsBox.value);
    myCharts.setOption(option);
})

window.addEventListener("resize",() =>{
    location.reload()
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
    overflow: hidden;
}
.echarts{
    height: 100%;
}
</style>