<template>
  <div class="person">
    <ul>
      <li v-for="item in list" :key="item.id">
        {{ item.name }} -- {{ item.age }}岁
      </li>
    </ul>
  </div>
</template>

<script lang="ts" setup name="Person">
import { type Persons } from '@/types';
//defineProps(['list']); //只接收list
//接收list+限制类型
withDefaults(defineProps<{ list?: Persons }>(), {
  list:()=> [{ id: 'aaaaaa', name: '康师傅', age: 19 }]
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