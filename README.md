# vue-demo
# Vue2 → Vue3 Migration Examples
본 프로젝트는 Vue 2 기반 예제를 Vue 3 스타일로 리팩터링한 자료입니다.  
기능 추가 없이, 기존 동작과 화면을 그대로 유지하면서 코드 구조를 Vue 3 문법으로 전환했습니다.

## E-01-Instance 

### ✅ 변경 요약 (E01Instance.vue)
- **data() → ref():**  
  Vue 2의 `data()` 옵션을 Vue 3의 `ref()` 함수로 대체,`message` 변수를 `ref('Vue!')`로 선언하여 반응형 데이터로 관리.

- **<script> → <script setup>:**    
  Vue 2의 `export default { ... }` 구조를 제거하고 Vue 3의 `<script setup>`을 사용해 컴포넌트 정의를 간소화.

- **name 옵션 제거:**    
  Options API에서 사용하던 `name: "E01Instance"` 속성이 제거. <script setup>을 사용하면 파일이름이 컴포넌트 이름으로 자동 설정
---

### 💡 실행 결과
![E-01-instance](./screenshots/E01.png)

## E-02-Reactive 

### ✅ 변경 요약

- **data() → ref():**    
  Vue 2의 `data()` 옵션을 Vue 3에서는 `ref()` 함수로 대체,`firstName`,`lastName`을 `ref()`로 선언해 반응형 상태로 관리.

- **computed 속성 변환:**    
  Vue 2의 `computed` 옵션을 Composition API의 `computed()` 함수로 변경,`fullName`을 `computed(() => \`\${firstName.value} \${lastName.value}\`)`로 선언.

- **mounted() → onMounted():**   
  라이프사이클 훅을 Composition API 문법으로 변경,`onMounted(() => { ... })`로 선언하여 동일한 타이밍에 동작.

- **this 제거:**    
  `<script setup>` 내부에서는 `this`를 사용하지 않음,`this.firstName` 대신 `firstName.value` 형태로 접근.

- **Composition API 도입:**    
  `import { ref, computed, onMounted } from 'vue'`를 통해  
  반응형 상태, 계산 속성, 라이프사이클 훅을 명시적으로 관리.

---

### 💡 실행 결과

<p align="center">
  <img src="./screenshots/E02-1.png" alt="Before change" width="45%" style="border-radius: 8px; margin-right: 10px;"/>
  <img src="./screenshots/E02-2.png" alt="After change" width="45%" style="border-radius: 8px;"/>
</p>

## 🧩 E-03-Binding 

### ✅ 변경 요약

- **Composition API 전환:**  
  Vue 2의 Options API(`data`, `methods`)를 Vue 3의 Composition API(`<script setup>`)로 전환.      
  →`import { ref } from 'vue'`를 통해 반응형 상태(`message`, `id`, `password`)를 명시적으로 선언.    
  → 불필요한 `export default` 및 `this` 참조 제거로 코드 구조 단순화.  

- **data() → ref():**    
  Vue 2의 `data()` 옵션을 Composition API의 `ref()`로 변환, `message`, `id`, `password`를 모두 `ref()`로 선언하여 반응형 상태로 관리.

- **메서드 정의 방식 변경:**  
  Vue 2의 `methods` 옵션 대신 Composition API 문법으로 함수 정의.  
  → `const updateMessage = () => { ... }` 형태로 선언.  
  → 버튼 클릭 시 `message.value = ${id.value} ${password.value}` 로 갱신.

- **이벤트 핸들러 변경:**  
  템플릿의 인라인 화살표 함수 `@click="() => { ... }"`를 제거하여 <script setup> 내부에 별도의 `updateMessage 함수`를 정의하여 참조하도록 변경.    
  → `@click="updateMessage"` 형태로 단순화. 

  
---

### 💡 실행 결과

![E-03-binding](./screenshots/E03.png)

## E-04-Directives

### ✅ 변경 요약

- **data() → ref():**    
  Vue 2의 `data()`에서 관리하던 `isVisible`, `count`, `items`를 Vue 3의 `ref()`로 선언하여 반응형 상태로 관리.  

- **이벤트 핸들러 분리:**    
  Vue 2 템플릿 내부의 인라인 로직(`@click="isVisible = !isVisible"`, `@click="count++"`)을  
  `toggleVisibility()`, `incrementCount()` 함수로 분리하여 `<script setup>` 내부에서 정의.  

- **`.value` 접근 방식 적용:**  
  `ref`로 선언된 변수 접근 시 `.value` 사용 (`isVisible.value`, `count.value++`).  
  → Vue 3의 Proxy 기반 반응형 시스템에 맞게 수정.

- **구조 간소화:**  
  `export default` 구문 제거 후 `<script setup>`으로 전환하여  
  불필요한 보일러플레이트 코드 제거 및 가독성 향상.

---

### 💡 실행 결과

<p align="center">
  <img src="./screenshots/E04.png" alt="Before change" width="45%" style="border-radius: 8px; margin-right: 10px;"/>
  <img src="./screenshots/E04-2.png" alt="After change" width="45%" style="border-radius: 8px;"/>
</p>

## example3
이 예제는 **부모 컴포넌트(ParentComponent.vue)**와  
**자식 컴포넌트(ChildComponent.vue)** 간의 **Props 전달과 Emit 이벤트 통신**을  
Vue 2 → Vue 3로 변환한 사례입니다.

### ✅ 변경 요약

- **data() → ref():**  
  부모 컴포넌트에서 `parentMessage`를 `ref()`로 선언해 반응형 상태로 관리.  

- **props 정의 방식 변경:**  
  자식 컴포넌트의 `props: ['message', 'id', 'password']`를  
  `defineProps()` 함수로 변경하여 타입 명시(`String`, `Number`)와 함께 선언.  

- **이벤트 전송(`emit`) 변경:**  
  Vue 2의 `$emit('custom-event', payload)` 구문을  
  `defineEmits(['custom-event'])`로 선언 후 `emit('custom-event', payload)`로 변경.  

- **`export default` 제거:**  
  두 컴포넌트 모두 `<script setup>` 문법을 사용하여  
  불필요한 보일러플레이트 코드 제거 및 가독성 향상.

- **컴포넌트 등록 방식 단순화:**  
  `<script setup>`에서는 `import ChildComponent from './ChildComponent.vue'`만으로  
  자동으로 템플릿 내에서 사용 가능.`components` 옵션 제거.


---

### 💡 실행 결과

![E05ParentComponent](./screenshots/E05.png)

## example 4

### 🧩 구성 개요
이 예제는 **부모 컴포넌트(ParentComponent.vue)**가    
**자식 컴포넌트 2개(ChildComponent1.vue, ChildComponent2.vue)**로 데이터를 전달하는  
**Provide / Inject** 패턴을  
Vue 2 → Vue 3 구조로 변환한 사례입니다.

---

### ✅ 변경 요약

- **provide() 옵션 → provide() 함수 (함수형 호출):**    
  Vue 2의 `provide()` 옵션에서 객체를 `return`하던 구조를,  
  Vue 3 Composition API의 `provide('key', value)` **함수형 호출 구조**로 전환.  
  `<script setup>` 내부에서 Key-Value 형태로 직접 데이터를 주입.

- **컴포넌트 등록 간소화:**    
  기존 Vue 2의 `components` 옵션 등록 방식이 사라지고,  
  `<script setup>` 내부에서 `import`만으로 `ChildComponent1`과 `ChildComponent2`가  
  자동 인식되어 템플릿에서 바로 사용 가능.


- **inject 옵션 → inject() 함수:**    
  Vue 2의 `inject: ['sharedMessage']`를
  Vue 3의 `const sharedMessage = inject('sharedMessage')`로 변경하여
  반응형 데이터로 수신.

- **반응형 흐름 단순화:**   
  부모에서 한 번 provide하면,
  자식1–자식2로 이어지는 모든 하위 컴포넌트에서 동일한 데이터 접근 가능.
  데이터 전달 경로를 단축하고 코드량을 최소화.

![E06ParentComponent](./screenshots/E06.png)

