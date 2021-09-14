# SQL 구문



## DML(Data Manipulation Language)

---

**INSERT**

* 단일행 INSERT문은 VALUES절을 포함하며, 한 번에 한 건만 입력된다.

* 칼럼명과 VALUES절의 값을 서로 1:1로 매핑해 기술한다.

* PIRMARY KEY 제약 또는 NOT NULL 제약이 지정된 칼럼은 NULL값 입력을 허용하지 않음

* CHAR, VARCHAR는 **"**와 함께 입력

  ```sql
  INSERT INTO PLAYER (PLAYER_ID, PLAYER_NAME, TEAM_ID, POSITION, HEIGHT, WEIGHT, BACK_NO)
  VALUES
  ('2002007', '박지성', 'K07', 'MF', 178, 73, 7);
  ```

* INTO절의 칼럼명은 생략할 수 있다. INTO절 칼럼명을 지정하지 않으면 테이블에 정의된 칼럼순서대로 VALUES절에 모든값을 빠짐없이 기술해야한다.

* INTO절의 칼럼명을 지정하는 편이 쿼리의 안정성 측면에서 바람직하다.

  ```sql
  INSERT INTO PLAYER
  VALUES 
  ('2002010','이청','K07','','BlueDragon','2002','MF',17,NULL,NULL,'1',180,69); 
  ```

* **INSERT**의 **VALUES절**에 **서브쿼리**가 들어갈 수 있음.

  *(PLAYER_ID값을 기존 값에 + 1한 값으로 데이터를 넣는 문장)*

  ```sql
    INSERT INTO PLAYER(PLAYER_ID, PLAYER_NAME, TEAM_ID)
    VALUES ((SELECT TO_CHAR(MAX(TO_NUMBER(PLAYER_ID)) + 1)
    FROM PLAYER), '홍길동', 'K06');
  ```

* **서브쿼리 값**이 **다중행**이면 한번에 **여러 건이 입력**된다.*(INTO절의 칼럼명과 SELECT절의 컬럼명의 개수가 같아야함.)*

* VALUES 자리에 SELECT문이 올 수 있음.

  ```sql
  INSERT INTO TEAM(TEAM_ID, REGION_NAME, TEAM_NAME, ORIG_YYYY,STADIUM_ID)
  SELECT REPLACE(TEAM_ID, 'K', 'A') AS TEAM_ID,
  	  REGION_NAME, REGION_NAME || ' 올스타' as TEAM_NAME, 2019 AS ORIG_YYYY,
  	  STADIUM_ID
  FROM TEAM
  WHERE REGION_NAME IN ('성남', '인천');
  ```

**UPDATE**

*  **UPDATE**문 형식

  `UPDATE 테이블명
       SET 수정할 칼럼명1 = 수정될 새로운 값1
       ,[수정할 칼럼명2 = 수정될 새로운 값2]
       ,[............]
   [WHERE 수정 대상 식별 조건식 ];`

* **UPDATE**문의 **SET절**에 **서브쿼리** 사용하기*(팀 테이블에서 **창단년도가 2000년** 이후인 **팀의 주소**를 **홈팀 경기장의 주소**로 수정)*

  ```sql
  UPDATE TEAM A
  SET A.ADDRESS = ( SELECT X.ADDRESS
                    FROM STADIUM X
                    WHERE X.HOMETEAM_ID = A.TEAM_ID)
  WHERE A.ORIG_YYYY > 2000;
  ```

* **UPDATE**문의 **WHERE절**에 **서브쿼리** 사용하기*(홈팀의 정보가 존재하는 경기장의 지역번호와 전화번호를 홈팀의 지역번호와 전화번호로 수정)*

  ```sql
  UPDATE STADIUM A
  SET(A.DDD, A.TEL) = (SELECT  X.DDD, X.TEL
                       FROM  TEAM X
                       WHERE  X.TEAM_ID = A.HOMETEAM_ID)
  WHERE  EXISTS (SELECT 1
                 FROM TEAM X
                 WHERE X.TEAM_ID = A.HOMETEAM_ID) ;
  ```

  *(TEAM테이블을 2번 조회해야하는 비효율이 있음. [MERGE](#MERGE)문을 사용하면 1번만 조회하면 됨.)*

**DELETE**

* **DELETE**문 형식 
  `DELETE [FROM] 테이블명
  WHERE [삭제 대상 식별 조건식];`

* **DELETE**문의 **WHERE절**에서 **서브쿼리** 사용하기*(선수 테이블에서 창단년도가 1980년 이전인 팀에 소속된 선수의 데이터를 삭제)*

  ```sql
  DELETE PLAYER A
  WHERE EXISTS (SELECT 1
                FROM TEAM X
                WHERE X.TEAM_ID = A.TEAM_ID
                AND X.ORIG_YYYY < 1980);
  ```

**MERGE**

* 새로운 행을 입력하거나, 기존 행을 수정하는 작업을 한번에 할 수 있다.

* MERGE 다음에 입력/수정돼야 할 타겟 테이블을 입력하고 USING절에 입력/수정에 사용할 소스테이블을 입력한다. ON절에는 타겟 테이블과 소스테이블간의 조인 조건식을 기술해, 입력/수정할 데상을 결정한다.

* ON 절의 조건에 따라 조인에 성공한 행들에 대해서는 WHEN MATCHED TEHN 아래 UPDATE 구문을 수행하고, 조인에 실패한 행들에 대해 WHEN NOT MATCHED TEHN 아래 INSERT 구문을 수행한다.

* MERGE문 형식 

  `MERGE
  	INTO 타겟 테이블명
  	USING 소스 테이블명  
  	ON (조인 조건식)
  	WHEN MATCHED THEN
  	UPDATE
  		SET 수정할 칼럼명1 = 수정될 새로운 값1, [수정할 칼럼명2 = 수정될 새로운 값2, ....]
  	WHEN NOT MATCHED THEN
  		INSERT [(칼럼1, 칼럼2, .....)]
  		VALUES (값1, 값2, .....,) ;`

**DDL과 DML의 처리 방식**

* **DDL(`CREATE, ALTER, RENAME, DROP`)** 명령어의 경우 데이터 구조 변경이 DDL 명령어 수행이 완료됨과 동시에 즉시 반영된다. *(롤백 안됨.)*
* **DML(`INSERT, UPDATE, DELETE, SELECT`)** 명령어 사용 시 데이터 변경 사항을 테이블에 영구적으로 저장하기 위해서는 COMMIT 명령어를 수행해 TRANSACTION을 종료해야한다.*(SQL PLUS는 반드시 COMMIT 해야함.)*

DQL SELECT

## TCL(Transaction Contrl Language)

---

* **트랜잭션 개요**

  * 데이터베이스의 논리적 연산단위다.

  * 밀접히 관련되어 분리될 수 없는 한 개 이상의 데이터베이스 조작을 가리킨다.

  * 하나의 트랜잭션에는 하나 이상의 SQL 문장이 포함된다.

  * 분할 할 수 없는 최소의 단위이다. 그러므로 전부 적용 or 전부 취소한다.

    *(은행에서 계좌이체 상황을 연상하면 트랜잭션을 이하하는데 도움이 된다.*
    *계좌이체는 최소한 두 가지 이상의 작업으로 이루어져 있다.)*

  * 계좌이체 사례

    \- STEP1. 100번 계좌의 잔액에서 10,000원을 뺀다.

    \- STEP2. 200번 계좌의 잔액에 10,000원을 더한다.

  * 위의 두 작업중 하나라도 실패하는 경우 계좌이체는 원래의 금액을 유지해야한다.

* **트랜잭션 제어 명령어 TCL**

  1. **커밋(COMMIT)** : 올바르게 반영된 데이터를 데이터베이스에 반영시키는 것을 말한다.
  2. **롤백(ROLLBACK)** : 트랜잭션 시작 이전 상태로 되돌리는 것이다.
  3. **저장점(SAVEPOINT)** : 트랜잭션의 일부만 취소할 수 있게 만드는 명령어이다.

  \-  트랜잭션의 대상은 `UPDATE, INSERT, DELETE` 등 데이터를 변경하는 `DML 문`이다. 

* **트랜잭션의 특성**

  * 원자성
  * 일관성
  * 고립성
  * 지속성

* **COMMIT**

* 

## DDL(Data Definition Language)

---

* **Create Table**

  * 테이블과 컬럼의 정의

    \- 테이블에 존재하는 모든 데이터를 고유하게 식별할수 있으면서 반드시 값이 존재하는 기본키 칼럼을 지정한다.

    \- 기본키는 단일 칼럼이 아닌 여러 개의 칼럼으로 구성될 수 있다.*(복합키)* 
    \- 테이블과 테이블 간에 정의된 관게는 기본키와 외부키를 활용해서 설정하도록 한다.

  * 테이블 생성 구문
    **CREATE　TABLE　테이블이름 (**

    ​	**칼럼명1 DATATYPE [DEFAULT 값] [NOT NULL],
    ​	칼럼명2 DATATYPE [DEFAULT 값]** **[NOT NULL]****,**

    ​	**칼럼명2 DATATYPE [DEFAULT 값]** **[NOT NULL],
    ​	............**

    **) ;**

  * 테이블 생성시 주의 할 규칙

    \- 테이블 병은 의미있는 이름을 사용한다.

    \- 테이블 병은 다른 테이블의 이름과 중복되어서는 안된다.

    \- 한 테이블 내에서 칼럼명이 중복되게 지정될 수 없다.

    \- `테이블명 (칼럼명, 칼럼명, 칼럼명)` 테이블 이름을 지정하고 "()"안에 칼럼들을 지정, 칼럼은 ","로 구분한다. 

    \- 칼럼뒤에 테이터 타입은 꼭 지정해야한다.

    \- 테이블  명은 A-Z, a-z, 0-9, _, $, # 문자만 허용된다.

    \- 칼럼에 대한 제약 조건이 있으면 CONSTRAINT를 이용하여 추가할 수 있다.

  * **제약조건(CONSTRAINT)**

    * 사용자가 원하는 조건의 데이터만 유지하기 위한 즉, 데이터의 무결성을 유지하기 위한 데이터베이스의 보편적인 방법. 테이블의 특정 칼럼에 설정하는 제약이다.

    * 제약조건의 종류

      \- Primary Key(기본키) 

## DCL(Data Control Language)

---

* 유저를 생성하고 권한을 제어할수 있는 명령어

* 유저와 권한

  \- 새로운 유저를 생성하고, 생성한 유저에게 **공유할 테이블이나 기타 오브젝트에 대한 접근 권한만을 부여할 수 있다.**

  \- 대부분의 데이터 베이스는 **데이터 보호와 보안을 위해서 유저와 권한을 관리**하고 있다.

  \- Oracle을 설치하면 기본적으로 제공되는 유저들은 아래와 같다.

  ​	\- SCOTT

  ​	\- SYS

  ​	\- SYSTEM

* 유저생성과 시스템 권한 부여

**GRANT CONNECT, RESOURCE TO SQLD;** 로그인되고 테이블 생성!