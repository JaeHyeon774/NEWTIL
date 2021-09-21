<h1>Java Script</h1>

---

* JavaScript
  * HTML과 Server Script(Back-end) 사이에서 접속자의 마우스 클릭, 키보드 입력등 이벤트 처리를 주로 담당.
    * 출력(HTML+CSS) <---> 동작/이벤트(Javascript) <---> 데이터베이스 접속 처리(백앤드)
  * **<body>**에 **<script>**태그를 사용하여 javascript 작성 or  **<head>**태그사이에 **<script src = "~~.js">**태그를 사용하여 javascript 작성!

* 변수 선언

  * 변수에 할당되는 데이터에 따라 동적으로 타입이 할당, 자바는 타입이 철저하게 구분.

  * 변수 선언시 타입을 따로 지정하지 않음.

  * var, let(권장) 이용

    * var와 let의 차이.

      ```javascript
      var a = 100;
      var a = 20;
      let b = 100;
      let b = 20;
      ```

      *(위와 같이 작성시 let은 오류가 남. var는 변수 이름을 a로 여러번 만들 수 있지만 let은 변수 이름을 한번쓰면 다른 이름을 사용해야함.)*

      ![제목 없음](javascript.assets/%EC%A0%9C%EB%AA%A9%20%EC%97%86%EC%9D%8C.png)





## javascript 실행순서(A->C->B)

```javascript
<script>
    alert('A');
	setTimeout(function() {
        alert('B');
    },0);
	alert('C');
</script>
```



