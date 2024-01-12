<template>
    <div class="person">
        <h2>汽车信息：一辆{{ car }}车，价值{{ car.price }}万</h2>
        <button @click="changePrice">修改汽车的价格</button>
        <br>
        <h2>游戏列表：</h2>
        <ul>
            <li v-for="g in games" :key="g.id">{{ g.name }}</li>
        </ul>
        <button @click="changeFirstGame">修改第一个游戏的名字</button>
    </div>
</template>

<script lang="ts">
    export default{
        name:'person'
    }
</script>

<script lang="ts" setup>
    import {reactive} from 'vue'

    let car=reactive({brand:'奔驰',price:100})
    let games=reactive([
        {id:'001',name:'原神'},
        {id:'002',name:'lol'},
        {id:'003',name:'赛博'},
    ])

    function changePrice(){
        car.price+=10
        console.log(car.price)
    }

    function changeFirstGame(){
        games[0].name='流星蝴蝶剑'
    }
</script>