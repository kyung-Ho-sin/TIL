### 오늘 공부 목록
1. 서브쿼리

#### 서브쿼리
>서브쿼리는 SQL문을 실행하는 데 필요한 데이터를 추가로 조회하기 위해 SQL문 내부에서 사용하는 SELECT문을 의미합니다. 서브쿼리의 결과 값을 사용하여 기능을 수행하는 영역은 메인쿼리라고 부릅니다. 

#### 서브쿼리의 종류
1.Nested Query(중첩 쿼리)
```
SELECT (SELECT NAME FROM test) A FROM TEST
```
>SELECT절에 사용되는 서브쿼리 
2.Sub Query(서브 쿼리)
```
SELECT * FROM TEST WHERE NAME IN (SELECT NAME FROM TEST)
```
>서브쿼리의 명확한 사용처는 WHERE절에 사용되었을때
3.Inline View(인라인 뷰)
```
SELECT * FROM (SELECT * FROM TEST) TB
```
>FROM 절에 사용되는 쿼리 이다.
4.Scalar SubQuery(스칼라 서브쿼리)
```
SELECT (SELECT NAME FROM TEST LIMIT 1) A FROM TEST;
```
>위치에 따라 구분되는것이 아니라 결과에 따라 구분되는 용어이다.

#### 서브쿼리의 특징
1.서브쿼리는 연산자와 같은 비교 또는 조회 대상의 오른쪽에 놓이며 괄호()로 묶어서 사용한다.
2.특수한 몇몇 경우를 제외한 대부분의 서브쿼리에서는 ORDER BY절을 사용할 수 없다.
3.서브쿼리의 SELECT절에 명시한 열은 메인쿼리의 비교 대상과 같은 자료형과 같은 개수로 지정해야 한다.
4.서브쿼리에 있는 SELECT문의 결과 행 수는 함께 사용하는 메인쿼리의 연산자 종류와 호환 가능해야 한다.

#### 단일행 서브쿼리
>단일행 서크붜리는 실행 결과가 단 하나의 행으로 나오는 서브쿼리를 뜻한다.
```
SELECT * FROM EMP WHERE HIREDATE < (SELECT HIREDATE FROM EMP WHERE ENAME = 'SCOTT');
```
```
SELECT E.EMPNO, E.ENAME, E.JOB, E.SAL, D.DEPTNO, D.DNAME, D.LOC FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND E.DEPTNO = 20
AND E.SAL > (SELECT AVG(SAL) FROM EMP);
```
>위와 같은 쿼리문은 단일형 서브쿼리안에서 함수를 사용하는 형식이다.

#### 다중행 서브쿼리
>다중행 서브쿼리는 실행 결과 행이 여러 개로 나오는 서브쿼리를 가리킵니다.

##### 다중행 연산자의 종류
1.IN : 메인쿼리의 데이터가 서브쿼리의 결과 중 하나라도 일치한 데이터가 있다면 TRUE
2.ANY, SOME : 메인쿼리의 조건식을 만족하는 서브쿼리의 결과가 하나 이상이면 TRUE
3.ALL : 메인쿼리의 조건식을 서브쿼리의 결과 모두가 만족하면 TRUE
4.EXISTS : 서브쿼리의 결과가 존재하면(즉, 행이 1개 이상일 경우) TRUE

#### 다중열 서브쿼리
>다중열 서브쿼리는 서브쿼리의 SELECT절에 비교할 데이터를 여러 개 지정하는 방식이다. 
```
SELECT * FROM EMP WHERE (DEPTNO, SAL) IN (SELECT DEPTNO, MAX(SAL) FROM EMP GROUP BY DEPTNO);
```

#### 인라인 뷰
>FROM절에서 사용하는 서브쿼리를 인라인 뷰 라고도 부른다. 인라인 뷰는 특정 테이블 전체 데이터가 아닌 SELECT문을 통해 일부 데이터를 먼저 추출해 온 후 별칭을 주어 사용한다.
```
SELECT E10.EMPNO, E10.ENAME, E10.DEPTNO, D.DNAME, D.LOC FROM (SELECT * FROM EMP WHERE DEPTNO =10) E10, (SELECT * FROM DEPT) D
WHERE E10.DEPTNO = D.DEPTNO;
```

#### 스칼라 서브쿼리
>스칼라 서브쿼리는 SELECT절에 하나의 열 영역으로 결과를 출력하는 것을 의미한다. 주의점은 꼭 하나의 결과만 반환하도록 작성해야 한다.
```
SELECT EMPNO, ENAME, JOB, SAL, (SELECT GRADE FROM SALGRADE WHERE E.SAL BETWEEN LOSAL AND HISAL) AS SALGRADE, DEPTNO, (SELECT DNAME FROM DEPT WHERE E.DEPTNO = DEPT.DEPTNO) AS DNAME FROM EMP E;
```

#### 오늘 한 줄
>서브쿼리의 개념을 위주로 공부를 해봤다. 해당부분들은 실습을 좀 계속적으로 해야 완벽하게 이해할수 있을듯하다.
