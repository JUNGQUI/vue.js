### 뷰 인스턴스

뷰 인스턴스는 말 그대로 화면 자체를 구현할 때 쓰는 기본 단위이다.

```vue
<html>
<head>
  <title>Vue Sample</title>
</head>
<body>
<div id="app">
  {{ message }}
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.2/dist/vue.js"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      message: 'Hello Vue.js!'
    }
  });
</script>
</body>
</html>
```

스크립트를 통해 vue 를 import 하고 `Vue` 객체를 생성해서 엘리먼트를 지정, 안에 데이터로 message 를 전달하고 값은
`Hello Vue.js!` 를 전달한다.

이렇게 하면 화면 구성을 담당하는 html 내의 `app` 이라는 엘리먼트에 메시지로 해당 값이 전달되고 화면은 렌더링이 된다.

이 new Vue 안에 속성들은 현재 나열한 속성 외 `template`, `methods`, `created` 등도 있다.

> template: 화면상에 표기되는 html, css 등의 요소를 정의하는 속성이다.
> 
> method: 말 그대로 해당 뷰 내에서 사용할 메소드로 이벤트나 함수가 여기에 정의된다.
> 
> created: 생성되자마자 실행될 메서드, 라이프 사이클 내에서 초기 init 을 위해 정의할때 사용된다.

### 뷰 라이프사이클

1. 인스턴스 생성
   - beforeCreate : 인스턴스 생성 전으로 data, method 와 같은 인스턴스 속성도 없고 dom 에 접근도 못한다. 캐시등에서 회원 정보를 파악 후 튕겨내는 로직이 있다면 이 사이클에서 실행된다.
   - created : 속성 생성. 이 단계에서 data init 과 같은 작업을 진행한다.
   - beforeMount : dom 을 그리기 전
   - mounted : dom 을 그려서 렌더링이 된 이후. 이 때부터 dom 요소에 대해 접근 및 데이터를 그릴 수 있다.
2. 인스턴스 - 화면 간 attached
   - beforeUpdate : 갱신이 이루어지기 전 작업, 해당 라이프 사이클에서 화면을 통해 프로그래스바를 표현하는 등 작업을 진행 할 수 있다.
   - updated : 갱신이 완료된 이후. 화면에 그린다던가 변경된 데이터를 통해 별도의 로직을 태우는 등의 작업이 진행된다.
3. 인스턴스 갱신
   - beforeDestroy : 인스턴스가 소멸하기 전 단계로 아직까지 dom 요소에 접근이 가능하기에 소멸 전 수행해야 하는 로직이 있다면 이 단계에서 수행할 수 있다.
   - destroyed : 소멸된 이후의 단계로 이미 인스턴스가 소멸했기 때문에 dom, 인스턴스 요소에도 접근이 불가능하다.
4. 인스턴스 소멸

