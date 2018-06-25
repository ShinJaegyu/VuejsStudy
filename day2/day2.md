Vue.js Study Day-2
===
2018.06.25

## Vue Router
### 싱글 페이지 어플리케이션
SPA (Single Page Application)
페이지를 이동할 때마다 웹페이지를 요청하여 새로 갱신하지 않고 미리 페이지를 받아놓고 페이지 이동 시에 클라이언트의 라우팅을 이용하여 화면을 갱신하는 패턴을 적용한 어플리케이션

### 라우팅
라우팅이란 웹 페이지 간의 이동 방법을 말한다.
라우팅을 이용하면 화면 간의 전환이 매끄럽고 애플리케이션 사용자 경험을 향상시킬 수 있다.

### Vue 라우터 사용하기
cdn에서 vue 라우터를 불러온다.
```html
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
```
라우팅 HTML 코드 예시
```html
<div id="app">
    <!-- URL값을 변경하는 태그-->
    <router-link to="/main">메인 컴포넌트로 이동</router-link>
    <router-link to="/login">로그인 컴포넌트로 이동</router-link>

    <!-- URL 값에 따라 갱신되는 화면 영역 -->
    <router-view></router-view>
</div>
```

라우팅 자바스크립트 코드 예시
```javascript
// 메인, 로그인 컴포넌트 정의
var Main = { template: '<div>main</div>' };
var Login = { template: '<div>login</div>' };

// URL에 맞춰 표시할 컴포넌트 지정
var routes = [
    { path: '/main', component: Main },
    { path: '/login', component: Login }
];

// Vue 라우터 정의
var router = new VueRouter({
    routes
});

// Vue 인스턴스에 라우터 추가
var app = new Vue({
    router
}).$mount('#app');

/* $mount() API
 * el속성과 동일한 역할을 한다.
 * 인스턴스에 el속성을 넣지 않았더라도 생성 후 $.mount를 통해 강제로 인스턴스를 화면에 붙일 수 있다.
 ```
---
## 네스티드 라우터
상위 컴포넌트 1개에 하위컴포넌트 1개를 포함하는 구조의 라우터이다.

## 네임드 뷰
같은레벨에서 여러개의 컴포넌트를 한 번에 표시하는 구조의 라우터이다.
