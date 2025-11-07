<template>
  <div>
    <p>Count: {{ count }}</p>
    <button @click="increment">Increment</button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const count = ref<number>(0); // ref로 원시 값 생성

const increment = () => {
  count.value++; // ref는 .value를 통해 값을 접근
};
</script>