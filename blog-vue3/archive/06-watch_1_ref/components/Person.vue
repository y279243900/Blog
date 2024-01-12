<template>
    <div class="person">
        <h1>情况一：监视【ref】定义的【基本类型】数据</h1>
        <h2>当前求和为：{{ sum }}</h2>
        <button @click="changeSum">增加</button>
    </div>
</template>


<script lang="ts">
// watch监视数据的变化
// vue3只能监视4种数据
// 1.ref定义的数据
// 2.reactive定义的数据
// 3.函数返回一个值（getter函数）
// 4.一个包含上述内容的数组
export default {
    name: 'person'
}
</script>

<script lang="ts" setup>
    import{ref,watch} from 'vue'
    
    let sum=ref(0)

    function changeSum(){
        sum.value+=1
    }
    // 情况一：监视【ref】定义的【基本类型】数据
    const stopWatch = watch(sum,(newValue,oldValue)=>{
        console.log('sum变化了',newValue,oldValue)
        if(newValue>10){
            stopWatch()
        }
    })
</script>