<template>
  <Person a="哈哈" :list="personList" />
  <MessageBoard />
</template>

<script lang="ts" setup name="App">
import Person from './components/Person.vue';
import MessageBoard from './components/MessageBoard.vue';
import { type PersonInter } from './types';
import { reactive } from 'vue'

let personList = reactive<PersonInter[]>([
  { id: 'akhdfkd', name: '小狗', age: 6 },
  { id: 'shi', name: '小兔', age: 18 },
  { id: 'jjkwfje', name: '小羊', age: 5, x: 2 }
])

console.log(personList)
</script>