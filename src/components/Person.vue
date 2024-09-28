<template>
  <div class="person">
    姓：<input type="text" v-model="lastName"><br>
    名：<input type="text" v-model="firstName"><br>
    全名：<span>{{ fullName }}</span>
    全名：<input type="text" :value="fullName"><br>
  </div>
</template>

<script lang="ts" setup name="Person">
import {computed, ref} from 'vue'

let lastName = ref("zhang")
let firstName = ref("san")
//计算属性，只读
let fullName = computed(() => {
  return lastName.value.slice(0,1).toUpperCase()+lastName.value.slice(1)+firstName.value;
})
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