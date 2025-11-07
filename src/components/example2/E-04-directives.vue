<template>
  <div class="container">

    <ul>
      <li v-for="item in items" :key="item.id">
        {{ item.name }} - {{ item.id }}
      </li>
    </ul>

    <div>
      <div v-if="isVisible">This is visible 1</div>
      <div :style="{ visibility: isVisible ? 'visible' : 'hidden' }">
        This is visible 2
      </div>
      <div v-show="isVisible">This is visible 3</div>
      <button @click="toggleVisibility">Toggle Visibility</button>
    </div>

    <div>
      <div v-text="count"></div>
      <div v-html="`<strong>${count}</strong>`"></div>
      <div v-pre>{{ count }}</div>

      <div id="div-1" v-if="count % 3 === 0"> count % 3 === 0</div>
      <div id="div-2" v-else-if="count % 2 === 0"> count % 2 === 0</div>
      <div id="div-4" v-else-if="count % 5 === 0"> count % 5 === 0</div>
      <div id="div-3" v-else>Count is not divisible by 2 or 3</div>

      <button @click="incrementCount">Increment Count</button>
    </div>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// 반응형 변수 정의 (data → ref)
const isVisible = ref(true)
const count = ref(0)
const items = ref([
  { id: 1, name: "Item 1" },
  { id: 2, name: "Item 2" },
  { id: 3, name: "Item 3" },
  { id: 4, name: "Item 4" },
])

// methods 분리 (템플릿의 직접 수정 로직 제거)
const toggleVisibility = () => {
  isVisible.value = !isVisible.value
}

const incrementCount = () => {
  count.value++
}
</script>

<style scoped>
.container {
  display: grid;
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  grid-gap: 20px;
}
</style>
