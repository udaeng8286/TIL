## Vue.js 

더보기

사용자 인터페이스 구축을 위한 JS 프레임워크

Web-App 만들 때 사용. 웹앱은 SPA이기 떄문에 화면 전환이 부드러움

### Vue 장점

1\. React와 Angular보다 사용이 쉬움

\- React는 지원하는 라이브러리가 더 많지만 Vue는 JS를 잘 다루지 못해도 구현이 좀 더 쉬움

2\. 코드를 작성할 때 rigth way가 있음 > 협업이 쉬움

\- React는 문법이 많지만 Vue는 방법이 하나

\- 초보일수록 쉬움

\- Vue 문법 몇개 외우면 초보도 output 쉽게 냄

\- 자유도 높은 개발가능

3\. HTML 랜더링 빠름

4\. 업데이트가 잘됨

### Vue의 핵심 기능

1\. 선언적 랜더링(Declarative Rendering)

\- 표준 HTML을 템플릿 문법으로 확장하여 JS 상태(State)를 기반으로 화면에 출력될 HTML을 선언적으로 작성할 수 있음  
2\. 반응성(Reactivity)

\- JS 상태(State) 변경을 추적하고, 변겨이 발생하면 DOM을 효울적으로 업데이트하는 것을 자동으로 수행

### Vue의 특징

**1\. Progressive Framework**

유연하고 점진적으로 채택할수 있도록 설계되었음

\- 빌드 과정 없이 정적 HTML에 적용

\- 모든 페이지에 웹 컴포넌트로 추가

\- SPA(Single-Page-Application)

\- Fullstack / SSR(Sever-Side-Rendering)

\- Jamstack / 정적 사이트 생성(SSG : Static-Site-Generation0

\- 데스크톱, 모바일, WebGL 또는 터미널을 대상으로 하는 경우

**2\. SPC : Single-File-Component**

\- 빌드 도구를 사용하는 대부분의 Vue 프로젝트에서는 HTML과 유사한 SPC(\*.vue 파일)라는 파일 형식을 사용하여 Vue 컴포넌트를 작성

\- 컴포넌트의 논리(JS), 템플릿(HTML), 스타일(CSS)을 하나의 파일에 캡슐화함

```
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>

<template>
  <button @click="count++">숫자 세기: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

**3\. API 스타일**

Vue 컴포넌트는 Option API와 Composition API 두 가지 스타일로 작성할 수 있음

**Option API**

\- 옵션의 data, methods, mounted 같은 객체를 사용하여 컴포넌의 로직 정의

\- 옵션으로 정의된 속성은 컴포넌트 인스턴스를 가리키는 함수 내부의 this에 노출

```
<script>
export default {
  // data()에서 반환된 속성들은 반응적인 상태가 되어 `this`에 노출됨
  data() {
    return {
      count: 0
    }
  },

  // methods는 속성 값을 변경하고 업데이트 할 수 있는 함수.
  // 템플릿 내에서 이벤트 리스너로 바인딩 될 수 있음.
  methods: {
    increment() {
      this.count++
    }
  },

  // 생명주기 훅(Lifecycle hooks)은 컴포넌트 생명주기의 여러 단계에서 호출됨
  // 이 함수는 컴포넌트가 마운트 된 후 호출됩니다.
  mounted() {
    console.log(`숫자 세기의 초기값은 ${ this.count } 입니다.`)
  }
}
</script>

<template>
  <button @click="increment">숫자 세기: {{ count }}</button>
</template>
```

**Composition API**

\- import해서 가져온 API 함수들을 사용하여 컴포넌트의 로직을 정의함

\- SFC에서 컴포지션 API는 일반적으로 <script setup>과 함께 사용

```
<script setup>
import { ref, onMounted } from 'vue'

// 반응적인 상태의 속성
const count = ref(0)

// 속성 값을 변경하고 업데이트 할 수 있는 함수.
function increment() {
  count.value++
}

// 생명 주기 훅
onMounted(() => {
  console.log(`숫자 세기의 초기값은 ${ count.value } 입니다.`)
})
</script>

<template>
  <button @click="increment">숫자 세기: {{ count }}</button>
</template>
```

**옵션 API와 컴포지션 API 비교**

**옵션 API**

일반적으로 OOP 언어 배경을 가진 사용자를 위한 클래스 기반 모델과 더 잘 맞는 "컴포넌트 인스턴스"(예제에서 볼 수 있는 this)의 개념을 중심

반응형 세부 사항을 추상화하고 옵션 그룹을 통해 코드 구조를 실행하여 초보자에게 더 친숙

**컴포지션 API**

함수 범위에서 직접 반응형 변수를 선언하고 복잡성을 처리하기 위해 여러 함수의 상태를 함께 구성하는데 중점

유연성하고 재사용하기 가능한 패턴을 작성이 가능

 보다 자유로운 형식이며 Vue에서 반응형이 효과적으로 사용되는 방식에 대한 이해가 필요
