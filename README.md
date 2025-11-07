[//]: # (# vue-demo)

[//]: # (# Vue2 → Vue3 Migration Examples)

[//]: # (본 프로젝트는 Vue 2 기반 예제를 Vue 3 스타일로 리팩터링한 자료입니다.  )

[//]: # (기능 추가 없이, 기존 동작과 화면을 그대로 유지하면서 코드 구조를 Vue 3 문법으로 전환했습니다.)

[//]: # ()
[//]: # (## 🔄 공통 변경사항 &#40;전체 컴포넌트 적용&#41;)

[//]: # ()
[//]: # (- **`<script>` → `<script setup lang="ts">`:**  )

[//]: # (  모든 컴포넌트에서 Vue 3의 Composition API를 사용하며,  )

[//]: # (  TypeScript를 적용하여 타입 안정성 확보.)

[//]: # ()
[//]: # (- **`export default` 제거:**  )

[//]: # (  `<script setup>` 문법 사용으로 불필요한 보일러플레이트 코드 제거.)

[//]: # ()
[//]: # (- **컴포넌트 자동 등록:**  )

[//]: # (  `components` 옵션 없이 `import`만으로 자동 등록.)

[//]: # ()
[//]: # (---)

[//]: # ()
[//]: # (## E-01-Instance )

[//]: # ()
[//]: # (### ✅ 변경 요약 &#40;E01Instance.vue&#41;)

[//]: # (- **data&#40;&#41; → ref&#40;&#41;:**  )

[//]: # (  Vue 2의 `data&#40;&#41;` 옵션을 Vue 3의 `ref&#40;&#41;` 함수로 대체,`message` 변수를 `ref&#40;'Vue!'&#41;`로 선언하여 반응형 데이터로 관리.)

[//]: # ()
[//]: # (- **<script> → <script setup>:**    )

[//]: # (  Vue 2의 `export default { ... }` 구조를 제거하고 Vue 3의 `<script setup>`을 사용해 컴포넌트 정의를 간소화.)

[//]: # ()
[//]: # (- **name 옵션 제거:**    )

[//]: # (  Options API에서 사용하던 `name: "E01Instance"` 속성이 제거. <script setup>을 사용하면 파일이름이 컴포넌트 이름으로 자동 설정)

[//]: # (---)

[//]: # ()
[//]: # (### 💡 실행 결과)

[//]: # (![E-01-instance]&#40;./screenshots/E01.png&#41;)

[//]: # ()
[//]: # (## E-02-Reactive )

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **data&#40;&#41; → ref&#40;&#41;:**    )

[//]: # (  Vue 2의 `data&#40;&#41;` 옵션을 Vue 3에서는 `ref&#40;&#41;` 함수로 대체,`firstName`,`lastName`을 `ref&#40;&#41;`로 선언해 반응형 상태로 관리.)

[//]: # ()
[//]: # (- **computed 속성 변환:**    )

[//]: # (  Vue 2의 `computed` 옵션을 Composition API의 `computed&#40;&#41;` 함수로 변경,`fullName`을 `computed&#40;&#40;&#41; => \`\${firstName.value} \${lastName.value}\`&#41;`로 선언.)

[//]: # ()
[//]: # (- **mounted&#40;&#41; → onMounted&#40;&#41;:**   )

[//]: # (  라이프사이클 훅을 Composition API 문법으로 변경,`onMounted&#40;&#40;&#41; => { ... }&#41;`로 선언하여 동일한 타이밍에 동작.)

[//]: # ()
[//]: # (- **this 제거:**    )

[//]: # (  `<script setup>` 내부에서는 `this`를 사용하지 않음,`this.firstName` 대신 `firstName.value` 형태로 접근.)

[//]: # ()
[//]: # (- **Composition API 도입:**    )

[//]: # (  `import { ref, computed, onMounted } from 'vue'`를 통해  )

[//]: # (  반응형 상태, 계산 속성, 라이프사이클 훅을 명시적으로 관리.)

[//]: # ()
[//]: # (---)

[//]: # ()
[//]: # (### 💡 실행 결과)

[//]: # ()
[//]: # (<p align="center">)

[//]: # (  <img src="./screenshots/E02-1.png" alt="Before change" width="45%" style="border-radius: 8px; margin-right: 10px;"/>)

[//]: # (  <img src="./screenshots/E02-2.png" alt="After change" width="45%" style="border-radius: 8px;"/>)

[//]: # (</p>)

[//]: # ()
[//]: # (## 🧩 E-03-Binding )

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **Composition API 전환:**  )

[//]: # (  Vue 2의 Options API&#40;`data`, `methods`&#41;를 Vue 3의 Composition API&#40;`<script setup>`&#41;로 전환.      )

[//]: # (  →`import { ref } from 'vue'`를 통해 반응형 상태&#40;`message`, `id`, `password`&#41;를 명시적으로 선언.    )

[//]: # (  → 불필요한 `export default` 및 `this` 참조 제거로 코드 구조 단순화.  )

[//]: # ()
[//]: # (- **data&#40;&#41; → ref&#40;&#41;:**    )

[//]: # (  Vue 2의 `data&#40;&#41;` 옵션을 Composition API의 `ref&#40;&#41;`로 변환, `message`, `id`, `password`를 모두 `ref&#40;&#41;`로 선언하여 반응형 상태로 관리.)

[//]: # ()
[//]: # (- **메서드 정의 방식 변경:**  )

[//]: # (  Vue 2의 `methods` 옵션 대신 Composition API 문법으로 함수 정의.  )

[//]: # (  → `const updateMessage = &#40;&#41; => { ... }` 형태로 선언.  )

[//]: # (  → 버튼 클릭 시 `message.value = ${id.value} ${password.value}` 로 갱신.)

[//]: # ()
[//]: # (- **이벤트 핸들러 변경:**  )

[//]: # (  템플릿의 인라인 화살표 함수 `@click="&#40;&#41; => { ... }"`를 제거하여 <script setup> 내부에 별도의 `updateMessage 함수`를 정의하여 참조하도록 변경.    )

[//]: # (  → `@click="updateMessage"` 형태로 단순화. )

[//]: # ()
[//]: # (  )
[//]: # (---)

[//]: # ()
[//]: # (### 💡 실행 결과)

[//]: # ()
[//]: # (![E-03-binding]&#40;./screenshots/E03.png&#41;)

[//]: # ()
[//]: # (## E-04-Directives)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **data&#40;&#41; → ref&#40;&#41;:**    )

[//]: # (  Vue 2의 `data&#40;&#41;`에서 관리하던 `isVisible`, `count`, `items`를 Vue 3의 `ref&#40;&#41;`로 선언하여 반응형 상태로 관리.  )

[//]: # ()
[//]: # (- **이벤트 핸들러 분리:**    )

[//]: # (  Vue 2 템플릿 내부의 인라인 로직&#40;`@click="isVisible = !isVisible"`, `@click="count++"`&#41;을  )

[//]: # (  `toggleVisibility&#40;&#41;`, `incrementCount&#40;&#41;` 함수로 분리하여 `<script setup>` 내부에서 정의.  )

[//]: # ()
[//]: # (- **`.value` 접근 방식 적용:**  )

[//]: # (  `ref`로 선언된 변수 접근 시 `.value` 사용 &#40;`isVisible.value`, `count.value++`&#41;.  )

[//]: # (  → Vue 3의 Proxy 기반 반응형 시스템에 맞게 수정.)

[//]: # ()
[//]: # (- **구조 간소화:**  )

[//]: # (  `export default` 구문 제거 후 `<script setup>`으로 전환하여  )

[//]: # (  불필요한 보일러플레이트 코드 제거 및 가독성 향상.)

[//]: # ()
[//]: # (---)

[//]: # ()
[//]: # (### 💡 실행 결과)

[//]: # ()
[//]: # (<p align="center">)

[//]: # (  <img src="./screenshots/E04.png" alt="Before change" width="45%" style="border-radius: 8px; margin-right: 10px;"/>)

[//]: # (  <img src="./screenshots/E04-2.png" alt="After change" width="45%" style="border-radius: 8px;"/>)

[//]: # (</p>)

[//]: # ()
[//]: # (## example3)

[//]: # (이 예제는 **부모 컴포넌트&#40;ParentComponent.vue&#41;**와  )

[//]: # (**자식 컴포넌트&#40;ChildComponent.vue&#41;** 간의 **Props 전달과 Emit 이벤트 통신**을  )

[//]: # (Vue 2 → Vue 3로 변환한 사례입니다.)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`data&#40;&#41;` → `ref<T>&#40;&#41;`:**  )

[//]: # (  부모 컴포넌트에서 `parentMessage`를 `ref<string>&#40;&#41;`로 선언해 반응형 상태로 관리.  )

[//]: # (  TypeScript 제네릭으로 타입 명시.)

[//]: # ()
[//]: # (- **`methods` → 일반 함수 선언:**  )

[//]: # (  `methods: { handleEvent&#40;payload&#41; { } }` 구문을  )

[//]: # (  `const handleEvent = &#40;payload: string&#41; => console.log&#40;payload&#41;`로 변경.  )

[//]: # (  함수 파라미터에 TypeScript 타입 추가.)

[//]: # ()
[//]: # (- **props 정의 방식 변경:**  )

[//]: # (  자식 컴포넌트의 `props: ['message', 'id', 'password']`를  )

[//]: # (  TypeScript `interface`로 타입 정의 후 `defineProps<Props>&#40;&#41;`로 선언.)

[//]: # ()
[//]: # (- **이벤트 전송&#40;`emit`&#41; 변경:**  )

[//]: # (  Vue 2의 템플릿 내 `$emit&#40;'custom-event', payload&#41;` 구문을  )

[//]: # (  `defineEmits<{ 'custom-event': [payload: string] }>&#40;&#41;`로 타입과 함께 선언.)

[//]: # ()
[//]: # (---)

[//]: # ()
[//]: # (### 💡 실행 결과)

[//]: # ()
[//]: # (![E05ParentComponent]&#40;./screenshots/E05.png&#41;)

[//]: # ()
[//]: # (## example4)

[//]: # (이 예제는 부모 컴포넌트&#40;ParentComponent.vue&#41;에서  )

[//]: # (자식 컴포넌트 2개&#40;ChildComponent1, ChildComponent2&#41;로  )

[//]: # (**Provide/Inject 패턴**을 통해 데이터를 전달하는  )

[//]: # (Vue 2 → Vue 3 Composition API 변환 사례입니다.)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`provide&#40;&#41;` → `provide&#40;&#41;` 함수:**  )

[//]: # (  부모 컴포넌트에서 `provide&#40;&#41; { return { sharedMessage: '...' } }` 구문을  )

[//]: # (  `provide&#40;'sharedMessage', 'Hello from provide'&#41;`로 변경.  )

[//]: # (  `vue`에서 `provide` 함수를 import하여 사용.)

[//]: # ()
[//]: # (- **`inject` → `inject<T>&#40;&#41;` 함수:**  )

[//]: # (  자식 컴포넌트에서 `inject: ['sharedMessage']` 배열 선언을  )

[//]: # (  `const sharedMessage = inject<string>&#40;'sharedMessage'&#41;`로 변경.  )

[//]: # (  TypeScript 제네릭으로 주입되는 값의 타입 명시.)

[//]: # ()
[//]: # (- **깊은 계층 구조에서의 데이터 전달:**  )

[//]: # (  ChildComponent1 → ChildComponent2로 이어지는 깊은 계층에서도  )

[//]: # (  props drilling 없이 `inject`로 직접 부모의 데이터 접근 가능.)

[//]: # ()
[//]: # (---)

[//]: # (![E06ParentComponent]&#40;./screenshots/E06.png&#41;)

[//]: # ()
[//]: # (## E-07-Options-API)

[//]: # (Options API → Composition API 변환 )

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`props` → `defineProps<T>&#40;&#41;` + `withDefaults&#40;&#41;`:**  )

[//]: # (  `props: { title: { type: String, default: '...' } }` 구문을  )

[//]: # (  `withDefaults&#40;defineProps<Props>&#40;&#41;, { title: 'User Information' }&#41;`로 변경.  )

[//]: # (  TypeScript interface로 타입 정의 후 기본값 설정.)

[//]: # ()
[//]: # (- **`data&#40;&#41;` → `ref<T>&#40;&#41;`:**  )

[//]: # (  `data&#40;&#41; { return { firstName: 'John', ... } }` 구문을  )

[//]: # (  각각 `const firstName = ref<string>&#40;'John'&#41;` 형태로 변경.  )

[//]: # (  모든 반응형 데이터를 개별 `ref&#40;&#41;`로 선언.)

[//]: # ()
[//]: # (- **`computed` → `computed&#40;&#41;`:**  )

[//]: # (  `computed: { fullName&#40;&#41; { return ... } }` 구문을  )

[//]: # (  `const fullName = computed&#40;&#40;&#41; => ...&#41;`로 변경.  )

[//]: # (  `vue`에서 `computed` 함수를 import하여 사용.)

[//]: # ()
[//]: # (- **`methods` → 일반 함수:**  )

[//]: # (  `methods: { greet&#40;&#41; { ... } }` 구문을  )

[//]: # (  `const greet = &#40;&#41; => { ... }`로 변경.  )

[//]: # (  화살표 함수 또는 일반 함수로 선언.)

[//]: # ()
[//]: # (- **`watch` → `watch&#40;&#41;`:**  )

[//]: # (  `watch: { greetCount&#40;newValue, oldValue&#41; { ... } }` 구문을  )

[//]: # (  `watch&#40;greetCount, &#40;newValue, oldValue&#41; => { ... }&#41;`로 변경.  )

[//]: # (  감시할 대상을 첫 번째 인자로 명시.)

[//]: # ()
[//]: # (- **Lifecycle Hooks 변경:**)

[//]: # (    - `beforeCreate`, `created` → `setup` 함수 본문 &#40;자동 실행&#41;)

[//]: # (    - `beforeMount` → `onBeforeMount&#40;&#41;`)

[//]: # (    - `mounted` → `onMounted&#40;&#41;`)

[//]: # (    - `beforeUpdate` → `onBeforeUpdate&#40;&#41;`)

[//]: # (    - `updated` → `onUpdated&#40;&#41;`)

[//]: # (    - `beforeUnmount` → `onBeforeUnmount&#40;&#41;`)

[//]: # (    - `unmounted` → `onUnmounted&#40;&#41;`)

[//]: # ()
[//]: # (- **`this` 키워드 제거:**  )

[//]: # (  Options API의 `this.firstName`, `this.greet&#40;&#41;` 등이  )

[//]: # (  Composition API에서는 직접 변수명으로 접근 &#40;`firstName.value`, `greet&#40;&#41;`&#41;.)

[//]: # ()
[//]: # (---)

[//]: # (![E07Options-API]&#40;./screenshots/E07.png&#41;)

[//]: # ()
[//]: # (## E-08-composition-api)

[//]: # (Composition API &#40;setup&#40;&#41; 함수&#41; → <script setup> 변환)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`setup&#40;props&#41;` 함수 → `<script setup>` 직접 선언:**  )

[//]: # (  `setup&#40;props&#41; { ... return { ... } }` 함수 전체를 제거하고  )

[//]: # (  변수와 함수를 최상위에 직접 선언. 자동으로 템플릿에 노출됨.)

[//]: # ()
[//]: # (- **`return` 문 제거:**  )

[//]: # (  `setup&#40;&#41;` 함수에서 사용하던 변수들을 명시적으로 `return`할 필요 없이  )

[//]: # (  선언만으로 템플릿에서 바로 사용 가능.)

[//]: # ()
[//]: # (- **`props` 매개변수 → `defineProps<T>&#40;&#41;`:**  )

[//]: # (  `setup&#40;props&#41;` 매개변수로 받던 props를  )

[//]: # (  `defineProps<Props>&#40;&#41;`와 `withDefaults&#40;&#41;`로 선언.)

[//]: # ()
[//]: # (- **TypeScript 타입 추가:**  )

[//]: # (  모든 `ref&#40;&#41;` 선언에 제네릭 타입 명시  )

[//]: # (  &#40;`ref<string>&#40;&#41;`, `ref<number>&#40;&#41;` 등&#41;.)

[//]: # ()
[//]: # (---)

[//]: # (![E08composition-api]&#40;./screenshots/E08.png&#41;)

[//]: # ()
[//]: # (## E-09-composition-API2)

[//]: # (Composition API &#40;이중 블록&#41; → <script setup>)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **이중 `<script>` 블록 → 단일 `<script setup>` 블록:**  )

[//]: # (  `<script>` &#40;name 정의용&#41;와 `<script setup>` &#40;로직용&#41; 이중 구조를  )

[//]: # (  단일 `<script setup lang="ts">` 블록으로 통합.  )

[//]: # (  `name` 옵션은 파일명으로 자동 추론되므로 제거.)

[//]: # ()
[//]: # (- **`defineProps&#40;&#41;` 타입 정의 방식 변경:**  )

[//]: # (  `defineProps&#40;{ title: { type: String, default: '...' } }&#41;` 구문을  )

[//]: # (  TypeScript interface + `withDefaults&#40;defineProps<Props>&#40;&#41;, { ... }&#41;`로 변경.)

[//]: # ()
[//]: # (- **불필요한 import 제거:**  )

[//]: # (  `defineProps`는 `<script setup>`에서 자동으로 사용 가능하므로  )

[//]: # (  명시적 import 불필요.)

[//]: # ()
[//]: # (- **TypeScript 타입 추가:**  )

[//]: # (  모든 `ref&#40;&#41;` 선언에 제네릭 타입 명시.)

[//]: # ()
[//]: # (---)

[//]: # (![E09composition-API2]&#40;./screenshots/E09.png&#41;)

[//]: # ()
[//]: # (## E-10-Ref)

[//]: # (Composition API &#40;setup&#40;&#41; 함수&#41; → <script setup> 변환)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`setup&#40;&#41;` 함수 → `<script setup>` 직접 선언:**  )

[//]: # (  `setup&#40;&#41; { ... return { ... } }` 함수 전체를 제거하고  )

[//]: # (  변수와 함수를 최상위에 직접 선언. 자동으로 템플릿에 노출됨.)

[//]: # ()
[//]: # (- **`return` 문 제거:**  )

[//]: # (  `setup&#40;&#41;` 함수에서 사용하던 `count`, `increment`를 명시적으로 `return`할 필요 없이  )

[//]: # (  선언만으로 템플릿에서 바로 사용 가능.)

[//]: # ()
[//]: # (- **TypeScript 타입 추가:**  )

[//]: # (  `ref&#40;&#41;` 선언에 제네릭 타입 명시 &#40;`ref<number>&#40;0&#41;`&#41;.)

[//]: # ()
[//]: # (---)

[//]: # (![E10Ref]&#40;./screenshots/E10.png&#41;)

[//]: # ()
[//]: # (## E-11-Reactive)

[//]: # (Composition API &#40;setup&#40;&#41; 함수&#41; → <script setup> 변환)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`setup&#40;&#41;` 함수 → `<script setup>` 직접 선언:**  )

[//]: # (  `setup&#40;&#41; { ... return { ... } }` 함수 전체를 제거하고  )

[//]: # (  변수와 함수를 최상위에 직접 선언. 자동으로 템플릿에 노출됨.)

[//]: # ()
[//]: # (- **`return` 문 제거:**  )

[//]: # (  `setup&#40;&#41;` 함수에서 사용하던 `person`, `incrementAge`를 명시적으로 `return`할 필요 없이  )

[//]: # (  선언만으로 템플릿에서 바로 사용 가능.)

[//]: # ()
[//]: # (- **TypeScript 인터페이스 추가:**  )

[//]: # (  `reactive&#40;&#41;` 객체의 타입을 명시하기 위해 `Person` 인터페이스 정의.  )

[//]: # (  `reactive<Person>&#40;{ ... }&#41;`로 타입 안정성 확보.)

[//]: # ()
[//]: # (- **reactive 특징:**  )

[//]: # (  `ref`와 달리 `.value` 없이 직접 속성 접근 가능 &#40;`person.age++`&#41;.)

[//]: # ()
[//]: # (---)

[//]: # (![E11Reactive]&#40;./screenshots/E11.png&#41;)

[//]: # ()
[//]: # (## E-12-Ref-Component)

[//]: # (Composition API &#40;setup&#40;&#41; 함수&#41; → <script setup> 변환)

[//]: # ()
[//]: # (### ✅ 변경 요약)

[//]: # ()
[//]: # (- **`setup&#40;&#41;` 함수 → `<script setup>` 직접 선언:**  )

[//]: # (  `setup&#40;&#41; { ... return { ... } }` 함수 전체를 제거하고  )

[//]: # (  변수와 함수를 최상위에 직접 선언. 자동으로 템플릿에 노출됨.)

[//]: # ()
[//]: # (- **`return` 문 제거:**  )

[//]: # (  `setup&#40;&#41;` 함수에서 사용하던 `inputField`, `focusInput`을 명시적으로 `return`할 필요 없이  )

[//]: # (  선언만으로 템플릿에서 바로 사용 가능.)

[//]: # ()
[//]: # (- **TypeScript 타입 추가:**  )

[//]: # (  DOM 요소 ref에 `Ref<HTMLInputElement | null>` 타입 명시.  )

[//]: # (  `ref<HTMLInputElement | null>&#40;null&#41;`로 선언하여 타입 안정성 확보.)

[//]: # ()
[//]: # (- **Template Ref 사용:**  )

[//]: # (  `ref&#40;null&#41;`로 선언한 변수명과 템플릿의 `ref="inputField"` 속성을 매칭하여  )

[//]: # (  DOM 요소에 직접 접근 가능.)

[//]: # ()
[//]: # (---)

[//]: # (![E12Ref-Component]&#40;./screenshots/E12.png&#41;)

# Vue2 → Vue3 Migration Examples

본 프로젝트는 Vue 2 기반 예제를 Vue 3 스타일로 리팩터링한 자료입니다.  
기능 추가 없이, 기존 동작과 화면을 그대로 유지하면서 코드 구조를 Vue 3 문법으로 전환했습니다.

## 🔄 공통 변경사항

모든 예제에 다음 변경사항이 공통으로 적용되었습니다:

| Vue 2 | Vue 3 |
|-------|-------|
| `<script>` | `<script setup lang="ts">` |
| `export default { ... }` | 제거 (불필요) |
| `components: { }` 옵션 | 자동 등록 |
| `this.property` | 직접 참조 (`property.value`) |
| `name` 옵션 | 파일명으로 자동 설정 |

---

## 📚 예제 목록

### E-01: Instance 기본
**핵심 개념:** Vue 인스턴스 생성 및 반응형 데이터

```javascript
// Vue 2
data() {
  return { message: 'Vue!' }
}

// Vue 3
const message = ref('Vue!')
```

![E-01-instance](./screenshots/E01.png)

---

### E-02: Reactive & Computed
**핵심 개념:** 반응형 상태, 계산 속성, 라이프사이클

**주요 변경:**
- `data()` → `ref()`
- `computed` 옵션 → `computed()` 함수
- `mounted()` → `onMounted()`

```javascript
// Vue 2
computed: {
  fullName() {
    return `${this.firstName} ${this.lastName}`
  }
}

// Vue 3
const fullName = computed(() => 
  `${firstName.value} ${lastName.value}`
)
```

<p align="center">
  <img src="./screenshots/E02-1.png" width="45%" style="border-radius: 8px; margin-right: 10px;"/>
  <img src="./screenshots/E02-2.png" width="45%" style="border-radius: 8px;"/>
</p>

---

### E-03: Data Binding
**핵심 개념:** 양방향 바인딩 및 이벤트 처리

**주요 변경:**
- `methods` 옵션 → 일반 함수 선언
- 인라인 핸들러 → 별도 함수로 분리

```javascript
// Vue 2
methods: {
  updateMessage() { ... }
}

// Vue 3
const updateMessage = () => { ... }
```

![E-03-binding](./screenshots/E03.png)

---

### E-04: Directives
**핵심 개념:** v-if, v-for, v-show 등 디렉티브 사용

**주요 변경:**
- 템플릿 인라인 로직 → 함수로 분리
- `.value` 접근 방식 적용

<p align="center">
  <img src="./screenshots/E04.png" width="45%" style="border-radius: 8px; margin-right: 10px;"/>
  <img src="./screenshots/E04-2.png" width="45%" style="border-radius: 8px;"/>
</p>

---

### E-05: Props & Emit
**핵심 개념:** 부모-자식 컴포넌트 간 통신

**주요 변경:**
- `props: ['message']` → `defineProps<Props>()`
- `$emit` → `defineEmits<Events>()`
- TypeScript 타입 정의 추가

```javascript
// Vue 2
props: ['message', 'id', 'password']

// Vue 3
interface Props {
  message: string
  id: string
  password: string
}
const props = defineProps<Props>()
```

![E-05-Props](./screenshots/E05.png)

---

### E-06: Provide & Inject
**핵심 개념:** 깊은 계층 구조에서의 데이터 전달

**주요 변경:**
- `provide() { return { } }` → `provide(key, value)`
- `inject: []` → `inject<T>(key)`

```javascript
// Vue 2
provide() {
  return { sharedMessage: 'Hello' }
}
inject: ['sharedMessage']

// Vue 3
provide('sharedMessage', 'Hello')
const sharedMessage = inject<string>('sharedMessage')
```

![E-06-Provide](./screenshots/E06.png)

---

### E-07: Options API → Composition API
**핵심 개념:** 전체적인 API 스타일 전환

**주요 변경:**

| 항목 | Vue 2 Options API | Vue 3 Composition API |
|------|------------------|---------------------|
| Props | `props: { }` | `defineProps<T>()` + `withDefaults()` |
| Data | `data() { }` | `ref<T>()` |
| Computed | `computed: { }` | `computed()` |
| Methods | `methods: { }` | 일반 함수 |
| Watch | `watch: { }` | `watch()` |
| Lifecycle | `mounted()` 등 | `onMounted()` 등 |

**라이프사이클 훅 매핑:**
- `beforeCreate`, `created` → setup 본문
- `beforeMount` → `onBeforeMount()`
- `mounted` → `onMounted()`
- `beforeUpdate` → `onBeforeUpdate()`
- `updated` → `onUpdated()`
- `beforeUnmount` → `onBeforeUnmount()`
- `unmounted` → `onUnmounted()`

![E-07-Options](./screenshots/E07.png)

---

### E-08: Composition API (setup 함수) → `<script setup>`
**핵심 개념:** setup() 함수 제거 및 코드 간소화

**주요 변경:**
- `setup(props) { ... return { } }` → 직접 선언
- `return` 문 불필요
- 자동 템플릿 노출

```javascript
// 변경 전
setup(props) {
  const count = ref(0)
  return { count }
}

// 변경 후
const count = ref<number>(0)
```

![E-08-Composition](./screenshots/E08.png)

---

### E-09: 이중 Script 블록 제거
**핵심 개념:** 단일 `<script setup>` 블록으로 통합

**주요 변경:**
- 이중 `<script>` + `<script setup>` → 단일 `<script setup>`
- `name` 옵션 제거

![E-09-Composition2](./screenshots/E09.png)

---

### E-10: Ref 사용법
**핵심 개념:** 단일 값의 반응형 상태 관리

```typescript
const count = ref<number>(0)
const increment = () => { count.value++ }
```

![E-10-Ref](./screenshots/E10.png)

---

### E-11: Reactive 사용법
**핵심 개념:** 객체의 반응형 상태 관리

**특징:** `.value` 없이 직접 속성 접근

```typescript
interface Person {
  name: string
  age: number
}

const person = reactive<Person>({
  name: 'John',
  age: 30
})

// 접근 시 .value 불필요
person.age++
```

![E-11-Reactive](./screenshots/E11.png)

---

### E-12: Template Ref
**핵심 개념:** DOM 요소에 직접 접근

```typescript
const inputField = ref<HTMLInputElement | null>(null)

const focusInput = () => {
  inputField.value?.focus()
}
```

```html
<input ref="inputField" />
```

![E-12-Ref-Component](./screenshots/E12.png)

---

## 🎯 핵심 학습 포인트

### 1. 반응형 시스템
- **ref:** 단일 값 (`.value`로 접근)
- **reactive:** 객체 (직접 접근)

### 2. Props & Events
- **Props:** `defineProps<T>()` + TypeScript 인터페이스
- **Emit:** `defineEmits<{ eventName: [param: Type] }>()`

### 3. 데이터 공유
- **Props/Emit:** 부모-자식 직접 통신
- **Provide/Inject:** 깊은 계층 간 통신

### 4. 타입 안정성
- 모든 `ref`, `reactive`에 TypeScript 타입 명시
- Props, Emit 이벤트 타입 정의

---

## 📝 참고사항

- 모든 예제는 기능 변경 없이 문법만 전환
- TypeScript를 통한 타입 안정성 확보
- `<script setup>`으로 보일러플레이트 최소화
- Composition API로 로직 재사용성 향상