<template>
    <div class="person">
        <h2>一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
        <button @click="changeBrand">修改汽车的品牌</button>
        <button @click="changePrice">修改汽车的价格</button>
        <button @click="changeCar">修改汽车</button>
    </div>
    <h2>当前求和为：{{ sum }}</h2>
    <button @click="changeSum">点我sum+1</button>
</template>

<script lang="ts" setup name="Person">
import { ref, reactive } from 'vue'
//数据
let car = reactive({ brand: '奔驰', price: 100 })
let sum = ref(0)
let isBenchi = 1;
function changePrice() {
    car.price += 10
}
function changeSum(){
    sum.value +=1
}
function changeBrand(){
    console.log(isBenchi);
    isBenchi = -isBenchi;
    console.log(isBenchi);
    car.brand = isBenchi>0?'奔驰':'宝马'
    console.log(car.brand);
}

function changeCar(){
    // car = {brand:'aaa',price:1}
    Object.assign(car,{brand:'aaa',price:1})
}

</script>

<style scoped>
.person {
    background-color: rgb(226, 241, 225);
    border-radius: 10px;
}

button {
    margin: 0 50px;
}
</style>