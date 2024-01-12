<template>
    <div class="person">
        <h2>姓名：{{ person.name }}</h2>
        <h2>年龄：{{ person.age }}{{ nl }}</h2>
        <button @click="changeName">修改姓名</button>
        <button @click="changeAge">修改年龄</button>
    </div>
</template>

<script lang="ts">
export default {
    name: 'person'
}
</script>

<script lang="ts" setup>
import { reactive, toRefs, toRef} from 'vue'

let person = reactive({name:"张三",age:18})

let {name,age}=toRefs(person)
let nl=toRef(person,'age')
console.log(nl.value)

function changeName(){
    name.value+='~'
    console.log(name.value,person.name)
}

function changeAge(){
    age.value+=1
    console.log(age.value,person.age)
}
</script>