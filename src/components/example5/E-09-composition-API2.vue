<template>
  <div>
    <h2>{{ title }}</h2>
    <p>Full Name: {{ fullName }}</p>
    <input v-model="firstName" placeholder="First Name" />
    <input v-model="lastName" placeholder="Last Name" />
    <button @click="greet">Greet</button>
    <p>Greeting Count: {{ greetCount }}</p>
    <p>{{ message }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, watch, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue';

// props 정의
interface Props {
  title?: string;
}

const props = withDefaults(defineProps<Props>(), {
  title: 'User Information'
});

// 반응형 상태 정의
const firstName = ref<string>('John');
const lastName = ref<string>('Doe');
const greetCount = ref<number>(0);
const message = ref<string>('');

// 계산된 속성
const fullName = computed(() => `${firstName.value} ${lastName.value}`);

// 메서드 정의
const greet = () => {
  greetCount.value++;
  message.value = `Hello, ${fullName.value}!`;
};

const resetGreetCount = () => {
  greetCount.value = 0;
};

// 감시자(watch) 설정
watch(greetCount, (newValue, oldValue) => {
  console.log(`Greet count changed from ${oldValue} to ${newValue}`);
  if (newValue >= 3) {
    message.value = "That's enough greetings for now!";
  }
});

// 라이프사이클 훅 정의
onBeforeMount(() => console.log('onBeforeMount hook'));
onMounted(() => console.log('onMounted hook'));
onBeforeUpdate(() => console.log('onBeforeUpdate hook'));
onUpdated(() => console.log('onUpdated hook'));
onBeforeUnmount(() => console.log('onBeforeUnmount hook'));
onUnmounted(() => console.log('onUnmounted hook'));
</script>