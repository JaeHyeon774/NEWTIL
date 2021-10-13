# JSTL

## 표현언어

---

* 기존 표현식보다 편리하게 값을 출력
* 변수와 여러가지 연산자를 포함할 수 있다.
* JSP의 내장 객체에 저장된 속성 및 자바의 빈 속성도 표현 언어에서 출력할 수 있다.
* 표현 언어 자체 내장 객체도 제공
* JSP페이지 생성시 기본 설정은 표현 언어를 사용할 수 없다.
* 페이지 디렉티브 태그에서는 반드시 isELIgnored=false로 설정해야한다.

| 구분          | 내장 객체        | 설명                                                         |
| ------------- | ---------------- | ------------------------------------------------------------ |
| 스코프        | pageScope        | JSP의 page와 같은 기능을 하고 page 영역에 바인딩된 객체를 참조한다. |
|               | requestScope     | JSP의 request와 같은 기능을 하고 request에 바인딩된 객체를 참조한다. |
|               | sessionScope     | JSP의 session과 같은 기능을 하고 session에 바인딩된 객체를 참조한다. |
|               | applicationScope | JSP의 application과 같은 기능을 하고 application에 바인딩된 객체를 참조한다. |
| 요청 매개변수 | param            | request.getParameter() 메서드를 호출한 것과 같으며 한개의 값을<br />전달하는 요청 매개변수를 처리한다. |
|               | paramValues      | request.getParameterValues() 메서드를 호출한 것과 같으며 여러 개의<br />값을 전달하는 요청 매개변수를 처리한다. |
| 헤더값        | header           | request.getHeader() 메서드를 호출한 것과 같으며<br />요청 헤더 이름의 정보를 단일 값으로 반환한다. |
|               | headerValues     | request.getHeader() 메서드를 호출한 것과 같으며<br />요청 헤더 이름의 정보를 배열로 반환한다. |
| 쿠키 값       | Cookies          | 쿠키 이름의 값을 반환한다.                                   |
| JSP 내용      | pageContext      | pageContext객체를 참조할 때 사용                             |
| 초기 매개변수 | initParam        | 컨텍스트의 초기화 매개변수 이름의 값을 반환한다.             |



* param 내장객체 사용 예

```jsp
<%= request.getParameter("id") %>
${param.id}
```

* requestScope 내장 객체 사용 예

```jsp
request.setAttribute("address", "인천광역시 부평구");
//포워딩한곳에서 받을 때
${requestScope.address}
```

* pageContext 내장 객체 사용 예

```jsp
http://localhost:8000/프로젝트명/페키지명/....
<%= request.getContextPath() %>/페키지명/....
${pageContext.request.contextPath}/페키지명/....
```

* 빈 사용

```jsp
${빈이름.속성이름}
```

* Collection 내장객체 사용 예

```jsp
${Collection객체이름[index].속성이름}
<sjp:useBean id="m1" class="sec01.ex01.MemberBean"/>
<jsp:setProperty name="m1" property="*"/>
<jsp:useBean id="membersList" class="java.util.ArrayList" />
<%
	MemberBean m2 = new MemberBean("son", "1234", "손흥민", "son@test.com");
	memberList.add(m1);
	memberList.add(m2);
%>
${memberList[0].id}
...
${memberList[1].id}
```

* has-a
  * 객체가 다른 객체의 속성을 가지는 경우를 has-a 관계라고 한다.
  * ${부모빈이름.자식속성이름.속성이름}



## 커스텀 태그

---

* JSP에서 액션 태그나 표현 언어를 사용할때 조건식이나 반복분에서 자바코드를 사용하고 있다. 이러한 자바코드를 제거하기 위해 JSTL이나 커스텀 태그가 등장했다.
* JSTL : JSP 페이지에서 가장 많이 사용하는 기능을 태그로 제공하며, JSTL 라이브러리를 따로 설치해서 사용한다.
* 개발자가 만든 커스텀 태그 : 개발자가 필요에 의해 만든 태그로, 스트러츠나 스프링 프레임워크에서 미리 만들어서 제공한다.



## JSTL(JSP Standard Tag Library)

---

| 라이브러리    | 세부 기능                                  | 접두어 | 관련 URI                               |
| ------------- | ------------------------------------------ | ------ | -------------------------------------- |
| 코어          | 변수 지원, 흐름 제어, 반복문 처리, URL처리 | C      | http://java.sun.com/jsp/jstl/core      |
| 국제화        | 지역, 메시지 형식, 숫자 및 날짜 형식       | fmt    | http://java.sum.com/jsp/jstl/fmt       |
| XML           | XML 코어, 흐름 제어, XML 변환              | x      | http://java.sum.com/jsp/jstl/xml       |
| 데이터 베이스 | SQL                                        | sql    | http://java.sum.com/jsp/jstl/sql       |
| 함수          | 컬렉션 처리, 문자열 처리                   | fn     | http://java.sum.com/jsp/jstl/functions |

[라이브러리 다운](http://tomcat.apache.org/download-taglibs.cgi)

#### Core 태그 라이브러리 사용하기

태그 라이브러리를 사용하려면  **반드시** JSP 페이지 상단에 taglib 디렉티브 태그를 추가해서 톰캣에 알려줘야한다.

<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>

| 기능      | 태그            | 설명                                                         |
| --------- | --------------- | ------------------------------------------------------------ |
| 변수지원  | \<c:set\>       | JSP 페이지에서 변수를 지정합니다.                            |
|           | \<c:remove\>    | 지정된 변수를 제거합니다.                                    |
| 흐름 제어 | \<c:if\>        | 조건문을 사용합니다.                                         |
|           | \<c:choose\>    | switch문을 사용하니다.<br />\<c:when\>과 \<c:otherwise\> 서브태그를 갖습니다. |
|           | \<c:forEach\>   | 반복문을 사용합니다.                                         |
|           | \<c:forTokens\> | 구분자로 분리된 각각의 토큰을 처리할 때 사용합니다.          |
| URL 처리  | \<c:import\>    | URL을 이용해 다른 자원을 JSP페이지에 추가합니다.             |
|           | \<c:redirect\>  | response.sendRedirect()기능을 수행합니다.                    |
|           | \<c:url\>       | 요청 매개변수로부터 URL을 생성합니다.                        |
| 기타 태그 | \<c:catch\>     | 예외 처리에 사용합니다.                                      |
|           | \<c:out\>       | JspWriter에 내용을 처리한 후 출력합니다.                     |

* \<c:set\>

```jsp
<c:set var="변수 이름" value="변수값" [scope="scope 속성 중 하나"]
<!--scope 속성 : page, request, session, application-->
```

* \<c:if\>

```jsp
<c:if test="${조건식}" var="변수이름" [scope="scope 속성 중 하나"]>
    ...
</c:if>
```

* \<c:choose\>

``` jsp
<c:choose>
    <c:when test="조건식1">내용1</c:when>
    <c:when test="조건식2">내용2</c:when>
    ...
    <c:otherwise test="조건식n">내용n</c:when>
</c:choose>
```

* \<c:forEach\>

```jsp
<c:forEach var="변수이름"items="반복할객체이름"begin="시작값"end="마지막값"step="증가값"varStatus="반복상태변수이름">
    ...
</c:forEach>
```

* \<c:redirect\>

```jsp
<c:redirect url="redirect할 URL">
    <c:param name="매개변수이름" value="전달값"/>
</c:redirect>
```

