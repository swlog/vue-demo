<!-- ParentComponent.vue -->
<template>
  <div>
    <ChildComponent1 />
  </div>
</template>

<script setup lang="ts">
import { provide } from 'vue'
import ChildComponent1 from "@/components/example4/ChildComponent1.vue"

// provide 사용 (기존 provide() 대체)
provide('sharedMessage', 'Hello from provide')

</script>
