# vue-demo
# Vue2 → Vue3 Migration Examples
본 프로젝트는 Vue 2 기반 예제를 Vue 3 스타일로 리팩터링한 자료입니다.  
기능 추가 없이, 기존 동작과 화면을 그대로 유지하면서 코드 구조를 Vue 3 문법으로 전환했습니다.

## Example 01 — Instance 

### ✅ 변경 요약 (E01Instance.vue)
- **data() → ref():**  
  Vue 2의 `data()` 옵션을 Vue 3의 `ref()` 함수로 대체,`message` 변수를 `ref('Vue!')`로 선언하여 반응형 데이터로 관리.

- **<script> → <script setup>** 
- Vue 2의 `export default { ... }` 구조를 제거하고 Vue 3의 `<script setup>`을 사용해 컴포넌트 정의를 간소화.

- **name 옵션 제거**
  Options API에서 사용하던 `name: "E01Instance"` 속성이 제거. <script setup>을 사용하면 파일이름이 컴포넌트 이름으로 자동 설정
---

### 💡 실행 결과
![E-01-instance](./screenshots/E01.png)
