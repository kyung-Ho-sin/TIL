### 오늘 공부 목록
1. SQL-99 표준문법
2. 서브쿼리

#### SQL-99 표준문법
>SQL문은 ISO/ANSI에서 관계형 데이터베이스 표준언어로 지정된 후 SQL-92를 거쳐 SQL-99 표준 문법이 나왔다. 해당 문법은 Oracle 9i 버전부터 지원하고 있으며 기존 JOIN문과 기능은 같지만 조인을 사용하는 문법에서 다소 차이가 있다.

1-1 NATURAL JOIN
```
SLECT E.EMPNO, E.ENAME, E.JOB, E.MGR, E.HIREDATE, E.SAL, DEPTNO, D.DNAME, D.LOC FROM EMP E NATURAL JOIN DEPT D
```
>등가조인(내부조인, 단순조인)과 같은 방식이다. 이 방식은 두 테이블에 이름과 자료형이 같은 열을 찾은 후 그 열을 기준으로 등가 조인을 해주는 방식>이다. 해당문법을 사용시에 주의점은 SELECT절에 명시할떄 테이블 이름을 붙이면 안되는 특성이 있다. (EX DEPTNO)
