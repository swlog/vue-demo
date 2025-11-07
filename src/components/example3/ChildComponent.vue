<template>
  <div>
    <p>{{ message }}</p>
    <p>{{ id }}</p>
    <p>{{ password }}</p>
    <button @click="emit('custom-event', 'Hello from child')">Send Event</button>
  </div>
</template>

<script setup lang="ts">
interface Props {
  message: string;
  id: number;
  password: number;
}

defineProps<Props>();
const emit = defineEmits<{
  'custom-event': [payload: string]
}>();
</script>