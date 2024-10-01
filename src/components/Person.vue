<template>
  <div class="person">
    <h1>中国</h1>
    <h2 ref="beijing">北京</h2>
    <h3>尚硅谷</h3>
    <button @click="showLog">点我输出h2这个元素</button>
  </div>
</template>

<script lang="ts" setup name="Person">
import {ref} from 'vue'
let beijing = ref(null)
function showLog(){
  console.log(beijing.value)
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