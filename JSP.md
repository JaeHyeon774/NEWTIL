# JSP

## JSP 구성요소

---

* **디렉티브 태그(Directive Tag)**
  * JSP 페이지에 대한 전반적인 설정 정보를 지정할 때 사용하는 태그.
* **페이지 디렉티브 태그** : JSP페이지의 전반적인 정보를 설절할 때 사용.

|     속성     |    기본값    |                             설명                             |
| :----------: | :----------: | :----------------------------------------------------------: |
|     info     |     없음     |              페이지를 설명해 주는 문자열을 지정              |
|   language   |    "java"    |              JSP 페이지에서 사용할 언어를 지정.              |
| contentType  | "text/html"  |                 JSP 페이지 출력 형식을 지정.                 |
|    import    |     없음     |    JSP 페이지에서 다른 패키지의 클래스를 임포트할 때 지정    |
|   session    |    "true"    |      JSP 페이지에서 HttpSession 객체의 사용 여부를 지정      |
|    buffer    |    "8kb"     |          JSP 페이지 출력 시 사용할 버퍼 크기를 지정          |
|  autoFlush   |    "true"    | JSP 페이지의 내용이 출력되기 전 버퍼가 다 채워질 경우 동작을 지정 |
|  errorPage   |   "false"    | JSP 페이지 처리 도중 예외가 발생할 경우 예외 처리 담당 JSP 페이지를 지정 |
| isErrorPage  |   "false"    |    현재 JSP 페이지가 예외 처리 담당 JSP 페이지인지를 지정    |
| pageEncoding | "ISO-8859-1" |         JSP 페이지에서 사용하는 문자열 인코딩을 지정         |
| inELIgnored  |    "true"    |      JSP 2.0 버전에서 추가된 기능으로 EL 사용 유무 지정      |

* **인클루드 디렉티브 태그** : 공통으로 사용하는 JSP 페이지를 다른 JSP 페이지에 추가할 때 사용

  * 페이지 상단에 화면이 바뀌더라도 고정되어 같은 기능을 하는 상단바나 메뉴바 JSP페이지를 미리 만들어놓고 다른 JSP페이지 요청시 **인클루드 디렉티브 태그**를 사용
  * `<%@ include file="공통기능.jsp" %>`

  ![KakaoTalk_20210930_225126515](C:/Users/JH/Desktop/KakaoTalk_20210930_225126515.jpg)

  

* **태그라이브 디렉티브 태그** : 개발자나 프레임워크에서 제공하는 태그를 사용할 때 사용.

* **스크립트 요소: 주석문, 스크립틀릿(Sxriptlet), 표현식, 선언식**
* **표현 언어**
* **내장 객체**
* **액션 태그**
* **커스텀 태그**

## JSP 스크립트 요소

---

* JSP 페이지에서 여러 가지 동적인 처리를 제동하는 기능.
* **<% %>** *(스크립틀릿)*기호 안에 자바 코드로 구현한다.
  * 선언문 : JSP에서 변수나 메서드를 선언할 때 사용.
  * 스크립틀릿 : JSP에서 자바 코드를 작성할 때 사용.
  * 표현식 : JSP에서 변수의 값을 출력할 때 사용.
* **선언문 사용하기**
  * JSP페이지에서 사용하는 멤버 변수나 멤버 메서드를 선언할 때 사용.
  * 선언문 안의 멤버는 서블릿 변환 시 서블릿 클래스의 멤버로 변환
  * 선언문의 형식 => `<%! 멤버 변수 or 멤버 메섣드 %>`
* **스크립틀릿 사용하기**
  * 스크립틀릿 형식 => `<% 자바코드 %>`
* **표현식 사용하기**
  * JSP 페이지의 정한 위치에 값을 출력하는 기능.
  * JSP 페이지에서 변수나 메서드의 결과값 등을 브라우저에 출력하는 용도
  * 표현식 형식 => `<%= 자바 변수 or 자바식 %>`
* 주석
  * HTML -> <!-- -->
  * JAVA -> /* */
  * JSP -> <%-- --%>

## 내장 객체(내장 변수) 기능

---

* JSP가 서블릿으로 변환될 때 컨테이너가 자동으로 생성시키는 서블릿 멤버 변수

| 내장 객체   | 서블릿             | 스코프                                                      |
| ----------- | ------------------ | ----------------------------------------------------------- |
| page        | this               | 한 번의 요청에 대해 하나의 JSP 페이지를 공유                |
| raquest     | HttpServletRequest | 한 번의 요청에 대해 같은 요청을 공유하는  JSP 페이지를 공유 |
| session     | HttpSession        | 같은 브라우저에서 공유                                      |
| application | ServletContext     | 같은 애플리케이션에서 공유                                  |

* ### session 데이터 바인딩 하기

```JSP
<%
HttpSession session = request.getSession() //세션 객체를 가져옴
session.setAttribute("name", "이순신"); <% //key : name, value : 이순신
String name = (String)session.getAttribute("name"); //세션 객체에 바인딩된 name 값을 가져옴 
%>
```

* ### application 데이터 바인딩하기

```JSP
<% 
//appTest1.jsp
session.setAttribte("name","이순신");
application.settAttribute("address","서울시 성북구");
//appTest1.jsp
String name = (String)session.getAttribute("name");
String address = (String)application.getAttribute("address");
%>
<%
	//application의 경우는 크롬과 익스플로럴 둘다 적용되지만 session은 같은 브러우저에서만 적용된다.
%>
```

* ### request 데이터 바인딩하기

```jsp
<% 
//request1.jsp
request.setAttribute("name","이순신");
request.setAttribute("address", "인천시 부평구");

RequestDispatcher dispatch = request.getRequestDispatcher("request2.jsp"); 
//request 객체를 다른 JSP로 포워딩 한다.
dispatch.forward(request,response);

//request2.jsp
String name = (String)requset.getAttribute("name");
String address = (String)request.getAttribute("address");
%>
```



## JSP welcome 파일 지정하기

---

* web.xml에 welcome 파일을 등록하면 페이지 요청시 제일 먼저 등록한 welcome 파일부터 차례로 찾아 홈페이지로 보여줌.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns="http://java.sun.com/xml/ns/javaee" 
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" id="WebApp_ID" version="3.0">
	<welcome-file-list>
        <welcome-file>/test02/main.jsp</welcome-file>
        <welcome-file>/test02/add.jsp</welcome-file>
        <welcome-file>/test02/add.html</welcome-file>
    </welcome-file-list>
</web-app>
```

