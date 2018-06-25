Vue.js Study Day-3
===
2018.06.25

## Vue Http 통신

### Vue resource
공식적으로 권장되던 라이브러리였으나 2016년 말에 지원 중단됨.

### Vue resource 사용하기
cdn에서 vue resource를 불러온다.
```html
<script src="https://cdn.jsdelivr.net/npm/vue-resource@1.5.1"></script>
```
```javascript
...
// URL 주소를 가져온다.
this.$http.get('URL주소')
.then(function(response){
    console.log(response);    
});
...
```
---
### Axios
엑시오스는 Vue 커뮤니티에서 가장 많이 사용되는 HTTP 통신 라이브러리이다.
또한 엑시오스는 Promise 기반의 API로 제공되어 별도의 로직을 구현할 필요 없이 주어진 API만으로도 원하는 로직을 구현할 수 있다.

### 엑시오스 사용하기
```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```
HTTP GET 요청
```javascript
axios.get('URL 주소').then().catch();
```
HTTP POST 요청
```javascript
axios.post('URL 주소').then().catch();
```
HTTP 요청에 대한 옵션 속성 정의
```javascript
axios({
    method: 'get',
    url: 'URL 주소'
});
```
