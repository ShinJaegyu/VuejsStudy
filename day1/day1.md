Vue.js Study Day-1
===
2018.06.20

## Vue.js
The Progressive JavaScript Framework
<https://vuejs.org>

---
## Vue.js 특징
* ##### Component 기반 프레임워크
* ##### 반응적 데이터 바인딩
    * Reactive Data Binding
* ##### Angular와 React의 장점들을 가져옴

---
## Vue.js 환경 세팅

### Node.js 설치
<https://nodejs.org/ko/download/>
### Vue.js devtools Chrome 플러그인 설치
<https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd>
### 에디터
* VSCODE
* Vue.js 관련 플러그인 설치

---
## Vue Instance
Vue 생성자로 생성된 뷰모델

### Vue 인스턴스 유효 범위
el속성으로 지정한 요소로 제한

### Vue 인스턴스 라이프 사이클

>* beforeCreate
>* created
>* beforeMount
>* mounted
>* beforeUpdate
>* updated
>* beforeDestroy
>* destroyed

---
## Vue Component 
화면 영역을 컴포넌트로 쪼개서 재사용 가능한 형태로 관리

### 전역 컴포넌트 등록
Vue 생성자에서 .component()를 호출하여 등록
```html
<my-component></my-component>
```
```javascript
Vue.component('my-component', {
    template : '<div>전역 컴포넌트가 등록되었습니다.</div>' 
});

new Vue({
    el : '#app',             
});
```
&lt;my-component&gt;태그가 my-component컴포넌트에 등록한 html로 변환된다.

### 지역 컴포넌트 등록

```javascript
var cmp = {
    template: '<div>지역 컴포넌트가 등록되었습니다.</div>'
};

new Vue({
    el : '#app',
    components: {
        'my-local-component': cmp
    }             
});
```

### 지역 컴포넌트와 전역 컴포넌트의 차이
전역 컴포넌트는 한 번 등록하면 어느 인스턴스에서나 사용가능
지역 컴포넌트는 새 인스턴스를 생성할 때마다 등록해줘야 함
>지역컴포넌트와 전역컴포넌트의 유효 범위의 차이

---
## Vue 컴포넌트 통신

### 상위에서 하위 컴포넌트로 데이터 전달

prop 속성을 사용하여 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달할 수 있다.

```html
<child-component v-bind:props 속성이름="상위 컴포넌트의 data 속성"></child-component>
```
```javascript
Vue.component('child-component',{
    props: ['prop 속성 이름']
});
```

### 하위에서 상위 컴포넌트로 이벤트 전달
event를 발생시켜 (event emit) 상위 컴포넌트에 신호를 보내면 된다.

```javascript
// 이벤트 발생
this.$emit('이벤트명');
```

```html
// 이벤트 수신
<child-component v-on:이벤트명="상위 컴포넌트의 메서스 명"></child-component>
```

### 관계 없는 컴포넌트 간 통신 - 이벤트버스

```javascript
// 이벤트 버스를 위한 추가 인스턴스 생성
var eventBus = new Vue();
```

```javascript
// 이벤트를 보내는 컴포넌트
...
methods: {
    메서드명: function() {
        eventBus.$emit('이벤트명',데이터);
    }
}
```

```javascript
// 이벤트를 받는 컴포넌트
...
methods: {
    created: function() {
        eventBus.$on('이벤트명',function(){
            ...
        });
    }
}
```