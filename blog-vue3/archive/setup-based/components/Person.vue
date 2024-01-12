<template>
    <div class="person">
        <h2>姓名：{{ name }}</h2>
        <h2>年龄：{{ age }}</h2>
        <button @click="changeName">修改名字</button>
        <button @click="changeAge">年龄+1</button>
        <button @click="showTel">查看联系方式</button>
    </div>
</template>

<script lang="ts">
    export default{
        name:'person'
    }
</script>

<script lang="ts" setup>
    import {ref} from 'vue'
    import { reactive } from 'vue'
    let name=ref("宝儿")
    let age=ref(23)
    let tel='138888888888'

    function changeName(){
        name.value="曾宝儿"
    }
    function changeAge(){
        age.value+=1
    }
    function showTel(){
        alert(tel)
    }
</script>