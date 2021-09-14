# 조인(JOIN)



## JOIN

---

* JOIN의 개요
  * 다른 정보가 들어있는 두 개 이상의 테이블을 연결해 데이터를 출력하는 것.
  * **PRIMARY KEY(PK)**나 **FOREIGN KEY(FK)**값의 연관에 의해 **JOIN**이 성립된다.
  * A, B, C, D 4개의 테이블을 조인할 경우 ((( A JOIN D ) JOIN C ) JOIN B )형식으로 조인한다.

*  **EQUI JOIN**의 형태

  * WHERE절에 JOIN 조건을 넣는다

  ```sql
  select p.player_name, t.team_name
  from player p, team t
  where p.team_id = t.team_id
  ```

* ANSI/ISO SQL 표준 방식으로 표현

  * ON 절에 JOIN 조건을 넣는다.

  ```sql
  select player.player_name, team.team_name
  from player inner join team
  on player.team_id = team.team_id;
  ```

  * "테이블명.칼럼명" 처럼 기술 하는 이유 :  두 테이블에 **같은 컬럼명**이 존재하기 때문에 DBMS의 옵티마이저가 어떤 칼럼을 사용해야할지 몰라 에러가 발생한다. 조회하는 데이터가 어느 테이블의 데이터인지 알 수 있게해줘 SQL의 **가독성**을 높이고 **유지보수성**을 높임

* **INNER JOIN**

  * JOIN 조건에서 동일한 값이 있는 행만 반환한다.

  * WHERE절에서 하던 JOIN조건을 FROM절에서 정의하겠다는 표시. USING조건절이나 ON조건절이 필수

    * WHERE절 JOIN조건

    ```sql
    SELECT EMP.DEPTNO, EMPNO, ENAME, DNAME
    FROM EMP, DEPT
    WHERE EMP.DEPTNO = DEPT.DEPTNO;
    ```

    * FROM절 JOIN조건

    ```SQL
    SELECT EMP.DEPTNO, EMPNO, ENAME, DNAME
    FROM EMP INNER JOIN DEPT
    ON EMP.DEPTNO = DEPT.DEPTNO;
    ```

* **NATURAL JOIN**

  * **두 테이블** 간의 **동일한 이름을 갖는 모든 칼럼**들에 대해 **EQUI(=) JOIN**을 수행한다.

  * **USING, ON 조건절, WHERE절**에서 **JOIN조건**을 **정의할 수 없다.**

  * **공통 칼럼(DEPTNO)**은 **ALIAS나 테이블 명과 같은 접두사를 붙일 수 없다.**

  * ```sql
    SELECT  A.EMPNO, A.ENAME, DEPTNO,B.DNAME
    FROM EMP A NATURAL JOIN DEPT B;
    ```

* **USING 조건절**

  * 

