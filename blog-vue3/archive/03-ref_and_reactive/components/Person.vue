<template>
    <div class="person">
        <h2>汽车信息：一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
        <button @click="changePrice">修改汽车的价格</button>
    </div>
</template>

<script lang="ts">
// 若需要一个基本类型的响应式数据，必须使用ref
// 若需要一个响应式对象，层级不深，ref、reactive都可以
// 若需要一个响应式对象，且层级较深，推荐使用reactive
export default {
    name: 'person'
}
</script>

<script lang="ts" setup>
import { reactive } from 'vue'
import { ref } from 'vue'

let car = ref({ brand: '奔驰', price: 100 })
let reactive_car = reactive({ brand: '奔驰', price: 100 })

function changePrice() {
    car.value.price += 10
    console.log(car.value.price)
}

function changPrice() {
    reactive_car.price += 10
    console.log(car.value.price)
}

</script>