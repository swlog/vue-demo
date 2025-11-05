<!--&lt;!&ndash; ChildComponent.vue &ndash;&gt;-->
<!--<template>-->
<!--  <div>-->
<!--    <p>{{ sharedMessage }}</p>-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  inject: ['sharedMessage']-->
<!--};-->
<!--</script>-->

<!--<style scoped>-->
<!--  p {-->
<!--    font-size: 1.5rem;-->
<!--  }-->
<!--</style>-->
<template>
  <div>
    <p>{{ sharedMessage }}</p>
  </div>
</template>

<script setup>
import { inject } from 'vue'

// Vue3 Composition API 방식의 inject
const sharedMessage = inject('sharedMessage')
</script>

<style scoped>
p {
  font-size: 1.5rem;
}
</style>
