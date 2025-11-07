<template>
  <div>Hello, {{ message }}</div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 반응형 변수 선언 (기존 data() 역할)
const message = ref('Vue!')
</script>

<style scoped>
div {
  color: blue;
}
</style>
