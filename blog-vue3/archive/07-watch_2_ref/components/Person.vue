<template>
    <div class="person">
        <h1>情况二：监视【ref】定义的【基本类型】数据</h1>
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
    import{ref,watch} from 'vue'
    
    let person = ref({
        name:'张三',
        age:18
    })

    function changeName(){
        person.value.name+='~'
    }

    function changeAge(){
        person.value.age+=1
    }

    function changePerson(){
        person.value={name:"请问",age:123}
    }
    // 监视，情况一：监视【ref】定义的【基本类型】数据，监视的是对象的地址值，若想监视对象内部属性的变化，需要手动开启深度监视
    // watch的第一个参数是：被监视的数据
    // watch的第二个参数是：监视的回调
    // watch的第三个参数是：配置对象（deeo，immediate）
    watch(person,(newValue,oldValue)=>{
        console.log(newValue,oldValue)
    },{deep:true})
</script>