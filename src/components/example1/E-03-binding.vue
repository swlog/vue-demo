<!--<template>-->
<!--  <div>-->
<!--    <input v-model="id" />-->
<!--    <input v-model="password" />-->
<!--    <p>{{ message }}</p>-->
<!--    <button @click="() => {-->
<!--      this.message = this.id + ' ' + this.password;-->
<!--    }">whoami</button>-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  name: "E03Binding",-->
<!--  data() {-->
<!--    return {-->
<!--      message: "Hello Vue",-->
<!--      id: '',-->
<!--      password: ''-->
<!--    };-->
<!--  }-->
<!--};-->
<!--</script>-->
<template>
  <div>
    <input v-model="id" />
    <input v-model="password" />
    <p>{{ message }}</p>
    <button @click="updateMessage">whoami</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// 반응형 변수 정의 (기존 data() 대체)
const message = ref('Hello Vue')
const id = ref('')
const password = ref('')

// 클릭 시 message 업데이트
const updateMessage = () => {
  message.value = `${id.value} ${password.value}`
}
</script>
