<template>
  <div class="person">
    <h1>情况一：监视ref定义的基本类型数据</h1>
    <h2>当前求和为：{{ sum }}</h2>
    <button @click="changeSum">点我sum+1</button>
    <h1>情况二：监视ref定义的对象类型数据</h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changePerson">修改人</button>
  </div>
</template>

<script lang="ts" setup name="Person">
import { ref, watch } from 'vue'
let sum = ref(0)
let person = ref({
  name: '张三',
  age: 18
})
function changeSum() {
  sum.value += 1
}
const stopWatchSum = watch(sum, (newValue, oldValue) => {
  console.log("sum变化了", newValue, oldValue)
  if (newValue >= 10) stopWatchSum();
})

function changeName() {
  person.value.name += '~'
}
function changeAge() {
  person.value.age += 1
}
function changePerson() {
  person.value = { name: '李四', age: 90 }
}
//监视情况一：监视的是对象的地址值
watch(person, (newValue, oldValue) => {
  console.log('person变化了', newValue, oldValue)
}, { deep: true, immediate: true })
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