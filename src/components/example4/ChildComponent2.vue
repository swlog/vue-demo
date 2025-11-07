<!-- ChildComponent2.vue -->
<template>
  <div>
    <p>{{ sharedMessage }}</p>
  </div>
</template>

<script setup lang="ts">
import { inject } from 'vue';

const sharedMessage = inject<string>('sharedMessage');
</script>

<style scoped>
p {
  font-size: 1.5rem;
}
</style>