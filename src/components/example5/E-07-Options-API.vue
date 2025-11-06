<!--<template>-->
<!--  <div>-->
<!--    <h2>{{ title }}</h2>-->
<!--    <p>Full Name: {{ fullName }}</p>-->
<!--    <input v-model="firstName" placeholder="First Name" />-->
<!--    <input v-model="lastName" placeholder="Last Name" />-->
<!--    <button @click="greet">Greet</button>-->
<!--    <p>Greeting Count: {{ greetCount }}</p>-->
<!--    <p>{{ message }}</p>-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  name: 'E07OptionsApi',-->

<!--  props: {-->
<!--    title: {-->
<!--      type: String,-->
<!--      default: 'User Information'-->
<!--    }-->
<!--  },-->

<!--  data() {-->
<!--    return {-->
<!--      firstName: 'John',-->
<!--      lastName: 'Doe',-->
<!--      greetCount: 0,-->
<!--      message: ''-->
<!--    };-->
<!--  },-->

<!--  computed: {-->
<!--    fullName() {-->
<!--      return `${this.firstName} ${this.lastName}`;-->
<!--    }-->
<!--  },-->

<!--  methods: {-->
<!--    greet() {-->
<!--      this.greetCount++;-->
<!--      this.message = `Hello, ${this.fullName}!`;-->
<!--    },-->
<!--    resetGreetCount() {-->
<!--      this.greetCount = 0;-->
<!--    }-->
<!--  },-->

<!--  watch: {-->
<!--    greetCount(newValue, oldValue) {-->
<!--      console.log(`Greet count changed from ${oldValue} to ${newValue}`);-->
<!--      if (newValue >= 3) {-->
<!--        this.message = "That's enough greetings for now!";-->
<!--      }-->
<!--    }-->
<!--  },-->

<!--  beforeCreate() {-->
<!--    console.log('beforeCreate hook');-->
<!--  },-->

<!--  created() {-->
<!--    console.log('created hook');-->
<!--  },-->

<!--  beforeMount() {-->
<!--    console.log('beforeMount hook');-->
<!--  },-->

<!--  mounted() {-->
<!--    console.log('mounted hook');-->
<!--  },-->

<!--  beforeUpdate() {-->
<!--    console.log('beforeUpdate hook');-->
<!--  },-->

<!--  updated() {-->
<!--    console.log('updated hook');-->
<!--  },-->

<!--  beforeUnmount() {-->
<!--    console.log('beforeUnmount hook');-->
<!--  },-->

<!--  unmounted() {-->
<!--    console.log('unmounted hook');-->
<!--  }-->
<!--};-->
<!--</script>-->

<!-- E07CompositionApi.vue -->
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
const props = defineProps({
  title: {
    type: String,
    default: 'User Information'
  }
});

// 반응형 변수
const firstName = ref('John');
const lastName = ref('Doe');
const greetCount = ref(0);
const message = ref('');

// 계산 속성
const fullName = computed(() => `${firstName.value} ${lastName.value}`);

// 메서드
function greet() {
  greetCount.value++;
  message.value = `Hello, ${fullName.value}!`;
}

function resetGreetCount() {
  greetCount.value = 0;
}

// watch
watch(greetCount, (newValue, oldValue) => {
  console.log(`Greet count changed from ${oldValue} to ${newValue}`);
  if (newValue >= 3) {
    message.value = "That's enough greetings for now!";
  }
});

// Lifecycle Hooks
console.log('beforeCreate hook (Composition API does not have this lifecycle directly)');
console.log('created hook (Composition API setup() executed)');

onBeforeMount(() => console.log('beforeMount hook'));
onMounted(() => console.log('mounted hook'));
onBeforeUpdate(() => console.log('beforeUpdate hook'));
onUpdated(() => console.log('updated hook'));
onBeforeUnmount(() => console.log('beforeUnmount hook'));
onUnmounted(() => console.log('unmounted hook'));
</script>
