### 오늘 공부목록 및 하루 일과
1. DB Inner Join Outer Join
2. 오후 2시 면접

#### DB Inner Join이란?
>내부조인(Inner Join)은 등가조인 및 단순조인 이라고도 한다. 테이블을 연결한 후에 출력 행을 각 테이블의 특정 열에 일치한 데이터를 기준으로 선정하는 방식이다.

 ```
 SELECT 컬럼명 FROM 테이블A, 테이블B WHERE 테이블A = 테이블B 
 ```
 >여러 테이블을 JOIN할때의 유의할점이 있다. 같은 컬럼명이 있을때를 조심해야 한다. 컬럼명이 같다면
 ```
 [Error]Execution: ORA-00918: 열의 정이가 애매합니다.
 ```
>이와 같은 오류가 발생할수 있다. 해당 오류를 피하기 위해선 어느 테이블에 존재하는 컬럼인지를 명확하게 해주는것이 중요하다.

#### DB Outer Join이란?
>