<!--&lt;!&ndash; ParentComponent.vue &ndash;&gt;-->
<!--<template>-->
<!--  <div>-->
<!--    <ChildComponent1 />-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->

<!--import ChildComponent1 from "@/components/example4/ChildComponent1.vue";-->

<!--export default {-->
<!--  name: "E06ParentComponent",-->
<!--  provide() {-->
<!--    return {-->
<!--      sharedMessage: 'Hello from provide'-->
<!--    };-->
<!--  },-->
<!--  components: {-->
<!--    ChildComponent1-->
<!--  }-->
<!--};-->
<!--</script>-->

<template>
  <div>
    <ChildComponent1 />
  </div>
</template>

<script setup>
import { provide } from 'vue'
import ChildComponent1 from "@/components/example4/ChildComponent1.vue"

// provide 사용 (기존 provide() 대체)
provide('sharedMessage', 'Hello from provide')
</script>
