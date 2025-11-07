# Vue 2 → Vue 3 Migration Guide

> Vue 2 기반 코드를 Vue 3 Composition API + TypeScript로 전환한 실습 프로젝트

## 📑 목차

- [프로젝트 개요](#-프로젝트-개요)
- [실행 방법](#-실행-방법)
- [공통 변경사항](#-공통-변경사항)
- [예제 목록](#-예제-목록)
    - [01. Instance](#01-instance---기본-인스턴스-생성)
    - [02. Reactive](#02-reactive---반응형-데이터)
    - [03. Binding](#03-binding---데이터-바인딩)
    - [04. Directives](#04-directives---디렉티브-활용)
    - [05. Props & Emit](#05-props--emit---부모자식-컴포넌트-통신)
    - [06. Provide & Inject](#06-provide--inject---의존성-주입)
    - [07. Options API](#07-options-api---옵션-api-전환)
    - [08. Composition API](#08-composition-api---setup-함수-방식)
    - [09. Composition API 2](#09-composition-api-2---이중-스크립트-블록)
    - [10. Ref (Primitive)](#10-ref-primitive---기본형-반응성)
    - [11. Reactive (Object)](#11-reactive-object---객체-반응성)
    - [12. Ref (Component)](#12-ref-component---dom-요소-접근)
- [주요 학습 포인트](#-주요-학습-포인트)
- [마이그레이션 체크리스트](#-마이그레이션-체크리스트)

---

## 📖 프로젝트 개요

본 프로젝트는 **Vue 2에서 Vue 3로의 마이그레이션 과정**을 단계별로 학습하기 위한 예제 모음입니다.

### 주요 특징

- ✅ 기존 기능과 화면을 동일하게 유지
- ✅ Vue 3 Composition API 적용
- ✅ TypeScript 타입 안정성 확보
- ✅ `<script setup>` 문법으로 간결한 코드 작성

---

## 🚀 실행 방법

```bash
# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 빌드
npm run build
```

---

## 🔄 공통 변경사항

모든 예제에 공통으로 적용된 Vue 3 마이그레이션 변경사항입니다.

### 1. `<script>` → `<script setup lang="ts">`
```vue
<!-- Vue 2 -->
<script>
export default {
  name: 'MyComponent',
  // ...
}
</script>

<!-- Vue 3 -->
<script setup lang="ts">
// export default 불필요
// TypeScript 타입 안정성 확보
</script>
```

### 2. 컴포넌트 자동 등록
```vue
<!-- Vue 2 -->
<script>
import ChildComponent from './ChildComponent.vue'

export default {
  components: {
    ChildComponent
  }
}
</script>

<!-- Vue 3 -->
<script setup lang="ts">
import ChildComponent from './ChildComponent.vue'
// components 옵션 불필요, import만으로 자동 등록
</script>
```

### 3. `this` 키워드 제거
```vue
<!-- Vue 2 -->
this.message = 'Hello'
this.increment()

<!-- Vue 3 -->
message.value = 'Hello'
increment()
```

---