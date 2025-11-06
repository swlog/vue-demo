<!--<template>-->
<!--  <div>{{ fullName }}</div>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  name: "E02Reactive",-->
<!--  data() {-->
<!--    return {-->
<!--      firstName: "Kyungsu",-->
<!--      lastName: "Lee"-->
<!--    };-->
<!--  },-->
<!--  mounted() {-->
<!--    setTimeout(() => {-->
<!--      this.firstName = "KSL";-->
<!--    }, 2000);-->
<!--  },-->
<!--  computed: {-->
<!--    fullName() {-->
<!--      return this.firstName + " " + this.lastName;-->
<!--    }-->
<!--  }-->
<!--};-->
<!--</script>-->
<template>
  <div>{{ fullName }}</div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

// 반응형 변수 정의 (기존 data() 대체)
const firstName = ref('Kyungsu')
const lastName = ref('Lee')

// computed 속성 변환
const fullName = computed(() => `${firstName.value} ${lastName.value}`)

// mounted 훅 변환
onMounted(() => {
  setTimeout(() => {
    firstName.value = 'KSL'
  }, 2000)
})
</script>
