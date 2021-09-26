<h1>Java Script</h1>

---

* JavaScript
  * HTML과 Server Script(Back-end) 사이에서 접속자의 마우스 클릭, 키보드 입력등 이벤트 처리를 주로 담당.
    * 출력(HTML+CSS) <---> 동작/이벤트(Javascript) <---> 데이터베이스 접속 처리(백앤드)
  * `<body>`에` <script>`태그를 사용하여 javascript 작성 or  `<head>`태그사이에 `<script src = "~~.js">`태그를 사용하여 javascript 작성!

* 변수 선언

  * 변수에 할당되는 데이터에 따라 동적으로 타입이 할당, 자바는 타입이 철저하게 구분.

  * 변수 선언시 타입을 따로 지정하지 않음.

  * 식별자 선언 규칙

    * 생성자 함수 이름은 항상 대문자로 시작.

    * 변수, 인스턴스, 함수, 메서드의 이름은 항상 소문자로 시작.

    * 여러 단어로된 식별자는 각 단어의 첫 글자를 대문자로 한다.

      

  * 식별자 종류

    * | 구분                  | 단독으로 사용                     | 다른 식별자와 사용      |
      | --------------------- | --------------------------------- | ----------------------- |
      | 식별자 뒤에 괄호 없음 | 변수 `let input`                  | 속성 `Array.length`     |
      | 식별자 뒤에 괄호 있음 | 함수 `prompt('Message','Defstr')` | 메서드 `Math.abs(-273)` |

  

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

* 사칙 연산자 주의 사항
  * 실수간의 뺄셈에서는 약간의 오차를 발생시킨다.
  * 어떤 숫자를 0으로 나누면 무한을 나타내는 값(Infinity)가 나온다.

## 함수

---

* 함수는 익명함수와 선언적 함수가 있다.

  * 익명 함수

    ```javascript
    function () {}
    ```

  * 선언적 함수

    ```javascript
    function 함수명() {}
    ```

* **콜백함수**

  * 매개변수로 전달되는 함수.

  ```javascript
  <script>
      function CallTenTimes(callback){
          for(var i = 0; i < 10; i++){
              callback();
          }
      }
  
      var callback = function () {
          alert(`함수 호출`);
      }
  
      CallTenTimes(callback);
  </script>
  ```

  * 콜백함수는 익명으로 쓰이는 경우가 더 많다.

  ```javascript
  <script>
      function callTenTimes (callback) {
      	for(var i = 0; i<10; i++){
          	callback();
          }
      }
  
  	callTenTimes(function () {
          alert(`함수 호출`);
      });
  </script>
  ```

## 객체

---

* 객체는 자료형 여러개를 한 번에 저장한다.

* 자바스크립트에서 거의 모든것이 객체이다.

* 배열도 객체의 타입으로 인식할 만큼 객체와 유사하다.

* 다른점이 있다면 배열은 인덱스와 요소가 있고, 객체는 이름과 값이 있다.

* 이름의 키를 사용하여 객체의 값에 접근한다.

* 객체는 배열처럼 하나 이상의 값을 가질 수 있다.

* **배열은 요소에 접근할 때 인덱스를 사용**하지만, **객체는 키를 사용**하여 접근한다.

* 객체 생성 예

  ```JAVASCRIPT
  let pruoduct = {
      제품명 : '7D 건조 망고',
      유형 : '당절임',
      성분 : '망고, 설탕, 메타중아산황나트륨, 치자황색소',
      원산지 : '필리핀'
  };
  ```

* 객체 속성 접근 예-1

  ```javascript
  product['제품명']
  product['유형']
  product['성분']
  product['원산지']
  ```

* 객체 속성 접근 예-2

  ```javascript
  product.제품명
  product.유형
  product.성분
  product.원산지
  ```

* for in 반복문을 사용하여 객체 요소를 하나씩 살펴 볼 수 있다.

  * `for (let 키 in 객체 { 문장 })`

  ```javascript
  for(let i in product){
      document.write(`${i} : ${product[i]}<br>`);
  }
  ```

  

## 속성과 메소드

---

* 배열 내부에 있는 값을 요소라고 하며, 객체 내부의 값을 속성이라 한다.
* 객채의 속성중 자료의 처리하는 속성을 메소드라고 부른다.
* 메소드 내에서 자신의 속성을 출력하고 싶을 때는 this 키워드를 사용한다.



## 프로토타입

---

* 생성자 함수로 생성된 객체가 공통으로 가지는 공간이다.
* 

## DOM(Document Object Model), 문서 객체 모델

---

* 문서 객체 모델을 조작할 수 있다. 즉 태그를 조작할 수 있다.

* 웹페이지의 실행 순서*(HTML코드를 위쪽에서 아래로 읽는다.)*

  ```javascript
  <script>
      document.querySelector('h1').style.backgroundColor = 'red';
  </script>
  <body>
      <h1>Process - 1</h1>
  </body>
  ```

  * 위에서 부터 읽어오기 때문에 오류가 발생한다. 아직 h1태그가 존재하지 않기 때문에 null에서 style 속성을 읽을 수 없다는 에러 메시지가 뜬다.

  ```javascript
  <body>
      <h1>Process - 1</h1>
      <script>
          document.querySelector('h1').style.backgroundColor = 'red';
      </script>
  </body>
  ```

  * 스크립트를 아래로 내리면 에러가 사라지지만 HTML 페이지가 방대하기 때문에 유지 보수가 힘들다.

  ```javascript
  <script>
      window.onload = function () {
      document.querySelector('h').style.backgroundColor = 'red';
  }
  </script>
  <body>
      <h1>Process - 1</h1>
  </body>
  ```

  * 이벤트를 이용하면 head에 javascript를 작성하여도 에러가 발생하지 않는다.

* **문서 객체 선택**
  * HTML태그를 javascript에서 문서 객체로 변환하는 것을 의미한다.

|      구분       | 메서드                                    | 설명                       |
| :-------------: | ----------------------------------------- | -------------------------- |
|  **1개 선택**   | `document.getElementById(아이디)`         | 아이디로 1개 선택          |
|                 | `document.querySelector(선택자)`          | 선택자로 1개 선택          |
| **여러개 선택** | `document.getElementsByName(이름)`        | name 속성으로 여러개 선택  |
|                 | `document.getElementsByClassName(클래스)` | class 속성으로 여러개 선택 |
|                 | ` document.querySelectorAll(선택자)`      | 선택자로 여러개 선택       |

## SPA(Single Page Application)

---

* 웹 페이지에서 틀만 있고 아무런 내용이 존재 하지 않는 페이지들은 처음에 틀만 받아오고 다른 것들은 javascript 사용자의 요청에 따라 웹 페이지의 내용을 바꾼다.
* 웹페이지를 여러번 요청하지 않아도 되서 서버의 부담이 줄어든다.
* 사용자가 웹 페이지를 이동할 때 새로 웹페이지를 읽어들이며 발생하는 깜빡임도 없어진다.

| 속성        | 설명                                                       |
| ----------- | ---------------------------------------------------------- |
| textContent | 문서 객체 내부 글자를 순수 텍스트 형식으로 가져오도록 변경 |
| innerHTML   | 문서 객체 내부 글자의 HTML태그를 반영해 가져오도록 변경    |



## Event 처리

* a태그로 자바스크립트를 호출하고 싶다면

  ```html
  <a href="javascript:sendit();">
  <!--javascript 생략 불가능-->
  ```

  

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



[OSI 7계층](https://present.do/shows/61443969e3562505806fa234?fbclid=IwAR2oowM7lZo0yGX68P46nePCznyhv233pFBXjSE1kPh9yFOtSFXzBMxkyxU&page=0)

