<!--&lt;!&ndash; ParentComponent.vue &ndash;&gt;-->
<!--<template>-->
<!--  <div>-->
<!--    <ChildComponent-->
<!--        :message="parentMessage"-->
<!--        :id="1"-->
<!--        :password="1234"-->
<!--        @custom-event="handleEvent"-->
<!--    />-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--import ChildComponent from './ChildComponent.vue';-->

<!--export default {-->
<!--  name: "E05ParentComponent",-->
<!--  data() {-->
<!--    return {-->
<!--      parentMessage: 'Hello from parent'-->
<!--    };-->
<!--  },-->
<!--  methods: {-->
<!--    handleEvent(payload) {-->
<!--      console.log(payload);-->
<!--    }-->
<!--  },-->
<!--  components: {-->
<!--    ChildComponent-->
<!--  }-->
<!--};-->
<!--</script>-->

<!-- E05ParentComponent.vue -->
<template>
  <div>
    <ChildComponent
        :message="parentMessage"
        @custom-event="handleEvent"
    />
  </div>
</template>

<script setup>
import { ref, defineOptions } from 'vue'
import ChildComponent from './ChildComponent.vue'


// 반응형 변수
const parentMessage = ref('Hello from parent')

// 메서드
const handleEvent = (payload) => {
  console.log(payload)
}
</script>
