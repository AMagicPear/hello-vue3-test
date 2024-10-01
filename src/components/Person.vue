<template>
  <div class="person">
    <h2>需求，当水温达到60度，或水位达到80cm时，给服务器发请求</h2>
    <h2>当前水温为：{{ temp }}℃</h2>
    <h2>当前水位为：{{ level }}cm</h2>
    <button @click="changeTemp">水温+10</button>
    <button @click="changeLevel">水位+10</button>
  </div>
</template>

<script lang="ts" setup name="Person">
import { ref, watch, watchEffect } from 'vue'
let temp = ref(10)
let level = ref(0)
function changeTemp() {
  temp.value += 10;
}
function changeLevel() {
  level.value += 10;
}

//监视
// watch([temp,level],(value)=>{
//   let [newTemp,newLevel] = value
//   if(newTemp>=60||newLevel>=80){
//     console.log('给服务器发请求')
//   }
// })

watchEffect(() => {
  if(temp.value>=60||level.value>=80){
    console.log('给服务器发请求')
  }
})

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