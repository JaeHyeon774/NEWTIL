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

