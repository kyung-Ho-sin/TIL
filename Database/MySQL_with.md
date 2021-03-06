## 오늘한 공부🙆‍♂

1. 프로그래머스 고득점Kit 문제풀기
2. 문제를 풀다 모르는 문법 찾아서 공부하기 (WITH 문법, @var = 2 와 @var :=2 문법의 차이)

### 1. 프로그래머스 고득점Kit 문제풀기
>이부분은 문제를 풀었다는 인증샷으로 대체를 하겠다.
![db_2020-11-12](https://user-images.githubusercontent.com/51444580/98896515-6f1d3900-24ec-11eb-9b0f-732a956d0cb8.PNG)
<br/>
>내일은 GROUP BY 마지막 문제와 IS NULL, JOIN 부분을 풀 생각이다.

### 2. WITH 문법 등등
>SET 문법을 오늘 알게 됬다. SET 문법은 변수를 만들때 사용하는 문법이다.
```
SET var = 1;
SET @var1 = 1;
```
>위에 문법을 보면 뭔가 다른 부분이 있을것이다. 맞다 @가 붙어있는 변수가 뜬금없이 나오고 있다.
>@가 의미하는 것은 프로시저가 실행이 끝나면 초기화가 되는데 @ 가 붙은 변수는 프로시저가 끝나도 계속 유지가 되는 값이된다. 

참조사이트 : [stackoverflow](https://stackoverflow.com/questions/1009954/mysql-variable-vs-variable-whats-the-difference)
```
SET var = 1;
SET @var1 = 1;

var = var + 1;
@var1 = var1 + 1;

ex) var var1
     2   2
     
    var var1
     2   3
```
>문제를 풀며 모르는 것들이 우수수 쏟아져 내렸다. 다음부분도 이번에 알게 된것이다. 바로 := 문법이다. 예를 들어 설명하겠다.
```
@var = 2;
@var1 := 3;
```
>해당 문법에 대해서는 아직 완벽하게 이해를 못했다. 이해한 부분까지만 설명을 하겠다.<br/>
>:= 문법을 붙이면 쿼리문 안에서도 사용할수 있다고 한다. 하지만 다른 사람들의 쿼리문을 보며 의문점이 생긴게 있다.
```
SET @HOUR_IT := -1;
SELECT ~~~
```
>위와 같이 사용한다는 것이다. := 는 쿼리문 안에서만 사용하는걸로 알고있었는데 밖에서 사용하는것을 보고 뭔가 싶다. 좀더 알아봐야할 내용이다.

>또 알게된 문법은WITH 문법이다. WITH문법은 임시테이블을 만들어주는 문법이다.<br>
```
WITH
E10 AS (SELECT * FROM EMP WHERE DEPTNO = 10),
D AS (SELECT * FROM DEPT)
SELECT E10.EMPNO, E10.ENAME, E10.DEPTNO, D.DNAME, D.LOC FROM E10, D WHERE E10.DEPTNO = D.DEPTNO;
```
>ORACLE 에서 WITH문법은 FROM절에 너무 많은 서브쿼리를 지정하거나 할때 가독성을 위해 사용하기도 한다. 주로 사용할때는 별칭을 정해서 사용한다.
>MySQL 에서는 WITH문법을 지원하지 않는다. 대신 WITH RECURSIVE를 지원해준다. 해당부분은 좀더 공부한후 내일 더 많은 내용을 정리해서 올려야 할듯하다.

### 오늘 한줄
>DB문제를 푸는데 진짜 기초적인것들도 많이 모른다고 생각이 많이든다. 내일은 서브쿼리와 WITH문법에 대해서 공부하고 기록할것이다.😜

