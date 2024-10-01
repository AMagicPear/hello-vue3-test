<template>
  <div class="person">

  </div>
</template>

<script lang="ts" setup name="Person">
import { type PersonInter} from "@/types/index";
// let person:PersonInter = {id:'dsfghsrht',name:'张三',age:60}
let personList:PersonInter[] = [
  { id: 'akhdfkd', name: '小狗', age: 60 },
  { id: 'shi', name: '小兔', age: 18 },
  { id: 'jjkwfje', name: '小羊', age: 5 }
]
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