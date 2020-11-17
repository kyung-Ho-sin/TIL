### 오늘 공부 목록
1. SQL-99 표준문법

#### SQL-99 표준문법
>SQL문은 ISO/ANSI에서 관계형 데이터베이스 표준언어로 지정된 후 SQL-92를 거쳐 SQL-99 표준 문법이 나왔다. 해당 문법은 Oracle 9i 버전부터 지원하고 있으며 기존 JOIN문과 기능은 같지만 조인을 사용하는 문법에서 다소 차이가 있다.

1-1 NATURAL JOIN
```
SLECT E.EMPNO, E.ENAME, E.JOB, E.MGR, E.HIREDATE, E.SAL, DEPTNO, D.DNAME, D.LOC 
FROM EMP E NATURAL JOIN DEPT D
```
>등가조인(내부조인, 단순조인)과 같은 방식이다. 이 방식은 두 테이블에 이름과 자료형이 같은 열을 찾은 후 그 열을 기준으로 등가 조인을 해주는 방식>이다. 해당문법을 사용시에 주의점은 SELECT절에 명시할떄 테이블 이름을 붙이면 안되는 특성이 있다. (EX DEPTNO)

1-2 JOIN ~ USING
```
FROM TABLE1 JOIN TABLE2 USING (조인에  사용한 기준열)
```
>JOIN~USING 또한 기존 등가 조인을 대신하는 방법이다. NATUAL JOIN이 자동으로 조인 기준열을 지정하는 것과 달리 USING키워드에 조인 기준으로 사용할 열을 명시해야 한다. 
```
SELECT E.EMPONO, E.ENAME, E.JOB, E.MGR, E.HIREDATE, E.SAL, E.COMM, DEPTNO, D.DNAME, D.LOC
FROM EMP E JOIN DEPT D USING (DEPTNO)
WHERE SAL >= 3000
ORDER BY DEPTNO, E.EMPNO;
```
>위의 SQL문은 JOIN~USING 예제이다. 해당문법을 사용할때도 NATUAL JOIN때와 같이 SELECT문에서 테이블 이름을 붙이지 않고 사용해야 한다.

1-3 JOIN ~ ON
```
FROM TABLE1 JOIN TABLE2 ON (조인 조건식)
```
>가장 범용성 있는 키워드이다. 기존 WHERE절에 있는 조인 조건식을 ON 키워드 옆에 작성한다.
```
SELECT E.EMPONO, E.ENAME, E.JOB, E.MGR, E.HIREDATE, E.SAL, E.COMM, E.DEPTNO, D.DNAME, D.LOC
FROM EMP E JOIN DEPT D ON (E.DEPTNO = D.DEPTNO) WHERE SAL <= 3000 ORDER BY E.DEPTNO, EMPNO;
```
>등가조인 방식을 JOIN~ON 방식으로 변경해서 작성한 것이다.
```
SELECT E1.EMPNO, E1.ENAME, E1.MGR, E2.EMPNO AS MGR_EMPNO, E2.ENAME AS MGR_ENAME 
FROM EMP E1 LEFT OUTER JOIN EMP E2 ON (E1.MGR = E2.EMPNO)
```
>왼쪽 외부 조인을 SQL-99문법으로 변경해서 작성한 것이다.
```
SELECT E1.EMPNO, E1.ENAME, E1.MGR, E2.EMPNO AS MGR_EMPNO, E2.ENAME AS MGR_ENAME 
FROM EMP E1 RIGHT OUTER JOIN EMP E2 ON (E1.MGR = E2.EMPNO)
```
>오른쪽 외부 조인을 SQL-99문법으로 변경해서 작성한 것이다.
```
SELECT E1.EMPNO, E1.ENAME, E1.MGR, E2.EMPNO AS MGR_EMPNO, E2.ENAME AS MGR_ENAME 
FROM EMP E1 PULL OUTER JOIN EMP E2 ON (E1.MGR = E2.EMPNO)
```
>전체 외부조인을 SQL-99문법으로 변경해서 작성한 것이다.
