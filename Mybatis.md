# Mybatis

## Mybatis 프레임 특징

---

* 한두줄의 자바코드로 DB 연동을 처리한다. 코드길이가 줄어들었다.
* SQL 명령어를 자바코드에서 분리하여 XML 파일에 따로 관리한다.
* 이식성이 좋아 어떤 프로그래밍 언어로도 구현이 가능
* 오픈소스이며 무료



## Mybatis 구성요소

1. Configuration 파일(sqlMapConfig.xml)

   \- Mybatis 메인 환경 설정을 정의

   \- DB설정및 mapper 설정등을 한다.

   \- DB 설정은 별도의 properties파일로 분리할 수 있다.

   \- mapper는 SQL squery를 xml 문서로 분리한 것이다.

2. 매퍼(Mapper)

   \- 두가지 종류의 매퍼를 정의 할 수 있다.

   \- 첫째는 SQL을 XML에 정의된 XML파일로 생성

   \- 두번재는 SQL을 메소드에 어노테이션으로 정의한 인터페이스로 생성

3. 매핑구문(Mapped Statements)

   \- SQL을 DB에 실행할 구문을 의미한다.

   \- 매핑 구문은 어노테이션 정의 방법과  XML정의 방식 두가지가 있다.

4. Mybatis

   \- SqlSession 는 Mapper xml에 등록된 SQL구분을 실행한다.
   \- SqlSession 객체는 SQL구분을 실행하기 위한 여러가지 메소드를 제공한다. selectOne(), selectList(), insert(), update(), delete() 등



## Mapper XML 파일 구조

---

* Mybatis 프레임워크에서 가장 중요한 파일
* SQL 문장을 가지고 있음.
* 

