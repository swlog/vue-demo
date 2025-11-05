<!--&lt;!&ndash; ChildComponent.vue &ndash;&gt;-->
<!--<template>-->
<!--  <h3> Child 1 </h3>-->
<!--  <div>-->
<!--    <p>{{ sharedMessage }}</p>-->
<!--  </div>-->

<!--  <h3> Child 2 </h3>-->
<!--  <div>-->
<!--    <ChildComponent2 />-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--import ChildComponent2 from "@/components/example4/ChildComponent2.vue";-->

<!--export default {-->
<!--  components: {ChildComponent2},-->
<!--  inject: ['sharedMessage']-->
<!--};-->
<!--</script>-->


<!--<style scoped>-->
<!--p {-->
<!--  color: red;-->
<!--}-->
<!--</style>-->

<template>
  <h3>Child 1</h3>
  <div>
    <p>{{ sharedMessage }}</p>
  </div>

  <h3>Child 2</h3>
  <div>
    <ChildComponent2 />
  </div>
</template>

<script setup>
import { inject } from 'vue'
import ChildComponent2 from "@/components/example4/ChildComponent2.vue"

// inject 사용 (Vue3 Composition API)
const sharedMessage = inject('sharedMessage')
</script>

<style scoped>
p {
  color: red;
}
</style>
