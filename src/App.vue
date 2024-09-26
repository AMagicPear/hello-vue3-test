<template>
  <Person/>
</template>

<script lang="ts">
import Person from './components/Person.vue';
// JS或TS
export default {
  name: 'App',  //组件名
  components:{Person} //注册组件
}
</script>