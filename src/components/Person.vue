<template>
  <div class="person">
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <h2>汽车：{{ person.car.c1 }}、{{ person.car.c2 }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changeC1">修改第一台车</button>
    <button @click="changeC2">修改第二台车</button>
    <button @click="changeCar">修改整个车</button>
  </div>
</template>

<script lang="ts" setup name="Person">
import { reactive } from 'vue';
let person = reactive({
  name: "张三",
  age: 18,
  car: {
    c1: '小米SU7',
    c2: '五菱宏光小煤球'
  }
})
//方法
function changeName() {
  person.name += '~';
}
function changeAge() {
  person.age += 1;
}
function changeC1() {
  person.car.c1 = "奥迪";
}
function changeC2() {
  person.car.c2 = '大众';
}
function changeCar() {
  person.car = { c1: '雅迪', c2: '爱玛' }
}
</script>

<style scoped>
.person {
  background-color: rgb(226, 241, 225);
  border-radius: 10px;
  padding: 5px 10px;
}

button {
  margin: 0 50px;
}
</style>