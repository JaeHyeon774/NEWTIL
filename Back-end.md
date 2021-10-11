# Back-end

## 웹 애플리케이션의 구성 요소

---

**C:\ai study\tomcat9\webapps\webShop\main.html**

| 구성요소 |                             기능                             |
| :------: | :----------------------------------------------------------: |
| webShop  | 웹 애플리케이션의 루트 디렉터리.<br /> 다른 웹 애플리케이션 이름과 중복을 허용하지 않으며,<br />여기에는 JSP HTML 파일이 저장된다. |
| WEB-INF  | 웹 애플리케이션에 관한 정보가 저장되는 곳. 이 디렉터리는 외부에서 접근할 수 없다. |
| classes  | 웹 애플리케이션이 수행하는 서블릿과 다른 일반 클래스들이 위치하는 곳. |
|   lib    | 웹 애플리케이션에서 사용되는 여러 가지 라이브러리 압축 파일(jar 파일)이 저장되는 곳.. <br />DB연동 드라이버나 프레임 워크 기능 관련 jar 파일이 여기에 저장된다. <br />lib 디렉터리의 jar는 클래스패스가 자동으로 설정된다. |
| web.xml  | 배치 지시자(deployment descriptor)로서 일종의 환경 설정 파일. <br />웹 애플리케이션에 대한 여러 가지 설정을 할 때 사용. |

* 웹 애플리케이션을 톰캣 컨테이너에 등록하는 방법

  1. %CATALINA_HOME%webApps 디렉터리에 애플리케이션을 저장

     \- 설치한 톰캣 루트 디렉터리의 하위 디렉터리인 webapps폴더에 작성한 웹 애플리케이션을 인식한 후 실행시키는 방법.

     \- 브라우저에서 웹 애플리케이션 요청

     * https://IP주소:포트번호/**컨텍스트**이름/요청파일이름
     * **컨텍스트란?** 
       * sever.xml에 등록하는 웹 애플리케이션을 **컨텍스트**라고 한다.

  2. server.xml에 직접 웹 애플리케이션을 등록

     \- 임의의 장소에 위치해 있는 웹 애플리케이션을 톰캣의 설정 파일인 server.xml에 등록해서 실행하는 방법.

     * **톰캣 컨테이너에 컨텍스트 등록하기**

       `<Context path="/컨텍스트 이름" docBase = "실제 웹 애플리케이션의 WEB-INF 디렉터리 위치" reloadable = "true 또는 false" />`

       `<Context path="/webMal" docBase="C:\\webShop" reloadable="true"/>`

| 구성 요소  |                             기능                             |
| ---------- | :----------------------------------------------------------: |
| path       | 웹 애플리케이션의 컨텍스트 이름이다. 웹 애플리케이션 이름과 다를 수도 있으며, <br />웹 프라우저에서 실제 웹 애플리케이션을 요청하는 이름이다. |
| docBase    | 컨텍스트에 대한 실제 웹 애플리케이션이 위치한 경로다.<br />**WEB-INF 상위 폴더까지의 경로**를 나타낸다. |
| reloadable | 실행 중 소스 코드가 수정될 경우 바로 갱신할지를 설정한다.<br />만약 false로 설정하면 톰캣을 다시 실행해야 추가한 소스 코드가 반영된다. |

## 톰캣 컨테이너에서의 웹 애플리케이션 동작 과정

![웹](Back-end.assets/%EC%9B%B9.jpg)

1. 웹 브라우저에서 컨텍스트 이름(webMal)으로 요청
2. 요청을 받은 톰캣 컨테이너는 요청한 컨텍스트 이름이 server.xml에 있는지 확인
3. 해당 컨텍스트 이름이 있으면 컨텍스트 이름에 대한 실제 웹 애플리케이션이 있는 경로로 가서 요청한 main.html을 클라이언트 웹 브라우저로 전송
4. 웹 브라우저는 전송된 main.html을 브라우저에 나타냄
