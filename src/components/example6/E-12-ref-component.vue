<template>
  <div>
    <input ref="inputField" type="text" placeholder="Click the button to focus" />
    <button @click="focusInput">Focus Input</button>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, type Ref } from 'vue';

const inputField: Ref<HTMLInputElement | null> = ref(null); // DOM 요소에 대한 ref 선언

const focusInput = () => {
  inputField.value?.focus();
};

onMounted(() => {
  console.log(inputField); // 컴포넌트가 마운트된 후, inputField에 접근 가능
  inputField.value?.focus();
});
</script>