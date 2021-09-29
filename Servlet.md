# Servlet

## Servlet이란?

---

* 서블릿은 서버쪽에서 실행되면서 클라이언트의 요청에 따라 동적으로 서비스를 제공하는 자바 클래스.
* 자바로 작성되므로 자바의 특성을 모두 가진다.
* 자바와 달리 독자적으로 실행되지 못하고 톰캣과 같은 JSP/Servlet 컨테이너에서 실행된다.
* 스레드 방식으로 실행된다.

![KakaoTalk_20210929_231341885](C:/Users/JH/Desktop/KakaoTalk_20210929_231341885.jpg)

| 서블릿 구성 요소         | 기능                                                         |
| ------------------------ | ------------------------------------------------------------ |
| Servlet  인터페이스      | javax.servlet 패키지에 선언되어 있다.<br />servlet 관련 추상 메서드를 선언한다.<br />init(), service(), destroy(), getServletInfo(), getServletConfig() |
| ServletConfig 인터페이스 | javax.servlet 패키지에 선언되어 있다.<br />Servlet 기능 관련 추상 메서드가 선언되어 있다.<br />getInitParameter(), getInitParameterNames(), getServletContext()<br />getServletName()이 선언되어 있다. |
| GenericServlet 클래스    | javax.servlet패키지에 선언되어있다.<br />상위 두 인터페이스를 구현하여 일반적인 서블릿 기능을 구현한 클래스<br />GenericServlet을 상속받아 구현한 사용자 서블릿은 사용되는 프로토콜에 따라 각각 service()를 오버라이딩해서 구현한다. |
| HttpServlet 클래스       | javax.servlet.http 패키지에 선언되어 있다.<br />GenericServlet을 상속받아 HTTP프로토콜을 사용하는 웹 브라우저에서 서블릿 기능을 수행한다.<br />웹 브라우저 기반 서비스를 제공하는 서블릿을 만들 때 상속받아 사용한다.<br />요청 시 service()가 호출되면서 요청 방식에 따라 doGet()이나 doPost()가 차례대로 호출된다. |

* **HttpServlet**의 여러 가지 메서드 기능

| 메서드                                                       | 기능                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| protected doDelete (HttpServletRequest req, HttpServletResponse resp) | 서블릿이 DELETE request를 수행하기 위해 service()를 통해서 호출됨. |
| protected doGet (HttpServletRequest req, HttpServletResponse resp) | 서블릿 Get request를 수행하기 위해 service() 를 통해서 호출됨. |
| protected doHead (HttpServletRequest req, HttpServletResponse resp) | 서블릿이 HEAD request를 수행하기 위해 service()를 통해서 호출됨. |
| prootected doPost (HttpServletRequest req, HttpServletResponse resp) | 서블릿이 Post request를 수행하기 위해  service()를 통해서 호출됨. |
| protected service (ServletRequest req, ServletResponse resp) | request를 public service()에서 전달받아 doXXX()메서드를 호출한다. |
| public service (ServletRequest req, ServletResponse resp)    | 클라이언트의 request를 protected service()에게 전달한다.     |

`public service() -> protected service() -> request 종류에 따른 doXXX() 메서드 호출`