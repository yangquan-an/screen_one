<template>
    <div class="box">
        <h4>
            中国地图
        </h4>
        <div class="echarts" ref="eare">

        </div>
    </div>
</template>

<script setup>
import chinaData from '../../public/map/china-cities.json'

import * as echarts from 'echarts'
import { onMounted,ref } from 'vue'

let eare = ref()

onMounted(() =>{

    echarts.registerMap('china',chinaData)

    let myChart = echarts.init(eare.value)

    myChart.setOption({
        geo:{
            map:'china',
            // 设置地图的样式
            itemStyle:{
                areaColor:"#0099ff",
                borderColor:"#00ffff",
                shadowColor:"rgba(230,130,70,0.5)",
                shadowBlur:30,
                emphasis:{
                    focus:"self" // 当前选中高亮，别的效果隐藏
                }
            },
           
        },
         // 设置地图的散点图
         tooltip:{
                trigger:"item"
            },
          series: [
                {
                    type:"scatter",
                    coordinateSystem:"geo", // 设置坐标类型
                    itemStyle:{
                        color:"red"
                    },
                    data:[
                       {name:"北京",value:[116.46,39.92,4367]},
                       { name:"上海",value:[121.48,31.22,8675]}
                    ]
                }
            ],

        visualMap:{
            type:"continuous",
            min:100,
            max:5000,
            calculable:true,
            inRange:{
                color:["#50a3ba","#eac736","#d94e5d"]
            },
            textStyle:{
                color:"#fff"
            }
        }
    })
})

</script>

<style scoped>
.box{
    height: 10.25rem;
    border: 1px solid blue;
    margin: .25rem;
    background: rgb(40, 137, 234,0.6);
    text-align: center;
    font-size: .4rem;
    color: white;
    overflow: hidden;
    padding: 50px 10px;
}
.echarts{
    width: 100%;
    height: 100%;
}
</style>