<template>
    <div id="box" ref="box">
        <header>
            <h1>大屏可视化项目</h1>
        </header>

        <!-- 主体区域 -->
        <div class="contrainer">
            <!-- 区域分成左中右 -->
            <div class="itemLeft">
                <page />
                <page1 />
            </div>
            <div class="itemCenter">
                <page2 />
            </div>
            <div class="itemRight">
                <page3 />
                <page4 />
            </div>
        </div>
    </div>
</template>


<script setup>
import { ref,onMounted } from 'vue';
import page from '../components/page.vue';
import page1 from '../components/page1.vue';
import page2 from '../components/page2.vue';
import page3 from '../components/page3.vue';
import page4 from '../components/page4.vue';

</script>



<style scoped lang="less">
#box{
    background: url('../assets/bg.jpg') top center no-repeat;
    background-size: cover;
    height: 100vh;
    width: 100vw;
    header{
        height: 1rem;
        width: 100%;
        line-height: 1rem;
        background: rgba(33, 92, 194, 0.6);
        h1{
            text-align: center;
            font-size: .5rem;
            color: white;
        }
    }
    .contrainer{
        // 设置最大 最小的一个宽度
        margin: 0px auto;
        background: rgba(240, 236, 236, 0.6);
        display: flex;
        .itemLeft,.itemRight{
            flex: 3;
        }
        .itemCenter{
            flex: 5;
        }
    }


}
</style>