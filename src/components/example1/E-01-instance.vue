<!--<template>-->
<!--  <div>Hello, {{ message }}</div>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  name: "E01Instance",-->
<!--  data() {-->
<!--    return {-->
<!--      message: "Vue!"-->
<!--    };-->
<!--  }-->
<!--};-->
<!--</script>-->

<!--<style scoped>-->
<!--div {-->
<!--  color: blue;-->
<!--}-->
<!--</style>-->

<template>
  <div>Hello, {{ message }}</div>
</template>

<script setup>
import { ref } from 'vue'

// 반응형 변수 선언 (기존 data() 역할)
const message = ref('Vue!')
</script>

<style scoped>
div {
  color: blue;
}
</style>
