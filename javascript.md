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



## 속성과 메소드

---

* 배열 내부에 있는 값을 요소라고 하며, 객체 내부의 값을 속성이라 한다.
* 객채의 속성중 자료의 처리하는 속성을 메소드라고 부른다.
* 메소드 내에서 자신의 속성을 출력하고 싶을 때는 this 키워드를 사용한다.

## 프로토타입

---

* 생성자 함수로 생성된 객체가 공통으로 가지는 공간이다.
* 

## DOM

---

* DOM은 구조화된 nodes와 property와 method를 갖고 있는 objects로 문서를 표현한다.
* 

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

