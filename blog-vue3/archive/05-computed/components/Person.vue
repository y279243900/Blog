<template>
    <div class="person">
        v-model双向修改，v-bind单向修改 <br>
        姓：<input type="text" v-model="firstName"> <br>
        名：<input type="text" v-model="lastName"> <br>
        <button @click="changeFullName">修改姓名</button>
        全名：<span>{{ fullName }}</span> <br>
    </div>
</template>

<script lang="ts">
export default {
    name: 'person'
}
</script>

<script lang="ts" setup>
    import {ref, computed} from 'vue'

    let firstName=ref("zeng")
    let lastName=ref("baoer")

    // 这么定义的fullName是一个计算属性，且是只读的
    // let fullName=computed(()=>{
    //     return firstName.value.slice(0,1).toUpperCase()+firstName.value.slice(1)+'-'+lastName.value
    // })

    // 这么定义的fullName是一个计算属性，且是可读可写的
    let fullName=computed({
    get(){
        return firstName.value.slice(0,1).toUpperCase()+firstName.value.slice(1)+'-'+lastName.value
    },
    set(val){
        const [str1,str2]=val.split('-')
        firstName.value=str1
        lastName.value=str2
    }
    })

    function changeFullName(){
        fullName.value= 'yang-yanjie'
    }

</script>