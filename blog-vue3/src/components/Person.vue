<template>
    <div class="person">
        <h1>情况三：监视【reactive】定义的【基本类型】数据</h1>
        <h2>姓名：{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changePerson">修改整个人</button>
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
    import{reactive,watch} from 'vue'
    
    let person = reactive({
        name:'张三',
        age:18
    })

    function changeName(){
        person.name+='~'
    }

    function changeAge(){
        person.age+=1
    }

    function changePerson(){
        Object.assign(person,{name:"请问",age:123})
    }
    // 情况三：监视【reactive】定义的【对象类型】数据,且默认是开启深度监视的
    watch(person,(newValue,oldValue)=>{
        console.log(newValue,oldValue)
    })
</script>