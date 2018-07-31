Vue.js Study Day-4
===
2018.07.31

## Vue Template
Vue 템플릿은 HTML,CSS등의 마크업 속성과 Vue 인스턴스에서 정의한 데이터 및 로직들을 연결하여 사용자가 브라우저에서 볼 수 있는 형태의 HTML로 변환해 주는 속성이다.

### Vue 인스턴스의 template속성으로 사용하기

```html
<script>
    new Vue({
        template:'<p>Hello {{ msg }}</p>'
    });
</script>
```

### &lt;template&gt;코드 사용하기
싱글 파일 컴포넌트 체계에서 사용한다.
```html
<template>
    <p>Hello {{ msg }}</p>
</template>
```

### 데이터 바인딩하기
데이터 바인딩에는 콧수염 괄호문법 {{ }}과 v-bind속성을 사용한다.

#### 콧수염 괄호 
data속성의 msg를 #app에 msg에 바인딩한다.
msg의 값이 변경되면 자동으로 갱신된다.
```html
<div id="app">
    <!-- data의 msg를 출력한다. -->
    {{ msg }}
    <!-- 자바스크립트 표현식도 쓸 수 있다. -->
    {{ msg.split('').reverse().join('') }}
</div>

<script>
    new Vue({
        el:'#app',
        data: {
            msg: 'Hello Vue.js'
        }
    });
</script>
```

데이터가 변경되도 값을 바꾸고 싶지 않을 때에는 v-once를 사용한다.

```html
<div id="app" v-once>
    {{ msg }}
</div>
```

#### v-bind
v-bind는 아이디, 클래스, 스타일 등 HTML 속성에 데이터를 바인딩할 때 사용한다.

```html
<div id="app">
    <div v-bind:id="idA">
    <div v-bind:class="classA">
    <div v-bind:style="styleA">
</div>

<script>
    new Vue({
        el:'#app',
        data: {
            idA: 10,
            classA: 'container',
            styleA: 'color: blue'
        }
    });
</script>
```

v-bind 디렉티브는 생략이 가능하다.

```html
<div id="app">
    <div :id="idA">
    <div :class="classA">
    <div :style="styleA">
</div>
```

### 디렉티브
Vue 디렉티브는 HTML태그 안에 v- 로 시작되는 모든 속성을 말한다.

<table>
    <thead>
        <tr>
            <th>디렉티브 이름</th>
            <th>역할</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                v-if
            </td>
            <td>
                데이터가 true이면 화면에 표시하고 false이면 표시하지 않는다.
            </td>
        </tr>
        <tr>
            <td>
                v-show
            </td>
            <td>
                데이터가 true이면 display:block 시키고 false이면 display:none 한다.
            </td>
        </tr>
        <tr>
            <td>
                v-for
            </td>
            <td>
                반복 출력할 때 사용한다.
            </td>
        </tr>
        <tr>
            <td>
                v-bind
            </td>
            <td>
                HTML속성을 바인딩할 때 사용한다.
            </td>
        </tr>
        <tr>
            <td>
                v-on
            </td>
            <td>
                이벤트를 처리할 때 사용한다. <br>
                <small>ex) v-on:click</small>
            </td>
        </tr>
        <tr>
            <td>
                v-model
            </td>
            <td>
                폼(form)에서 주로 사용한다.
                폼의 값과 데이터를 동기화 한다.
            </td>
        </tr>
    <tbody>
</table>

### 이벤트 처리
v-on 디렉티브와 methods 속성을 활용하여 이벤트를 처리한다.

```html
...
<button v-on:click="clickBtn(10)">버튼</button>
...

<script>
    ...
    methods:{
        clickBtn(i) {
            alert('clicked' + i);
        }
    }
    ...
</script>
```

v-on 디렉티브는 생략이 가능하다.
```html
...
<button @click="clickBtn(10)">버튼</button>
...
```

### computed 속성
데이터를 가공하는 등의 복잡한 연산은 계산된 속성을 사용한다.

```html
<div id="example">
  <p>원본 메시지: "{{ message }}"</p>
  <p>뒤집히도록 계산된 메시지: "{{ reversedMessage }}"</p>
</div>

<script>
    new Vue({
        el: '#example',
        data: {
            message: '안녕하세요'
        },
        computed: {
            // 계산된 getter
            reversedMessage: function () {
            // `this` 는 vm 인스턴스를 가리킵니다.
            return this.message.split('').reverse().join('')
            }
        }
    });
</script>
```