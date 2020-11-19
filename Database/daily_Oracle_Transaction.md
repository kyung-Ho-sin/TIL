### 오늘 공부목록
1.트랜잭션

### Transaction
>트랜잭션이란 더 이상 분할할 수 없는 최소 수행 단위를 뜻합니다. 트랜잭션은 어떠한 기능을 수행하는 SQL문 덩어리라고도 볼수있다. 트랜잭션을 제어하기 위해 사용하는 명령어를 TCL 이라고 한다.

1. 트랜잭션 정리<br/>
 1-1. 하나의 논리적 작업 단위를 구성하는 SQL문<br/>
 1-2. 트랜잭션를 데이터베이스에 확정 하는 방법 (Commit)<br/>
 1-3. 작업한 트랜잭션을 데이터베이스에서 취소하는 방법(Rollback)<br/>
 1-4. 트랜잭션 처리과정에서 오류가 발생하면 Aborted 상태로 트랜잭션의 시작 전 상태로 Rollback 작업을 한다.
2. 트랜잭션의 사용 이유<br/>
 2-1. 데이터의 일치성과 데이터 동시발생을 보장하기 위해서 사용한다.<br/>
3. 트랜잭션의 특징 <br/>
 3-1. 원자성 <br/>
 3-2. 일관성 <br/>
 3-3. 격리성 <br/>
 3-4. 지속성 <br/>
4.트랜잭션의 시작과 종료 <br/>
 4-1 시작 : 실행 가능한 SQL문장이 처음 실행될때 <br/>
 4-2 종료 <br/>
  4-2-1 Commit or Rollback <br/>
  4-2-2 DDL이나 DCL문장의 샐행(자동 Commit) <br/>
  4-2-3 장애발생 또는 시스템 충돌 <br/>
  4-2-4 deadlock 발생 <br/>
  4-2-5 사용자가 종료 <br/>
5. Commit <br/>
 5-1 INSERT, UPDATE, DELETE 문장 사용 후에 적용을 위해 사용
```
INSERT INTO PLAYER (PLAYER_ID, TEAM_ID, PLAYER_NAME, POSITION, HEIGHT,WEIGHT, BACK_NO) 
VALUES ('1997035', 'K02', '이운재', 'GK', 182, 82, 1); UPDATE PLAYER SET HEIGHT = HEIGHT + 10; 
COMMIT 
```
6. Rollback <br/>
 6-1 입력한 데이터, 수정한 데이터, 삭제한 데이터에 대하여 Commit 이전에 변경사항을 취소할 수 있는 기능 <br/>
 ```
 DELETE FROM TABLE1;
 
 ROLLBACK;
 ```
7.트랜잭션의 주의점 <br/>
 7-1. DML : Commit을 작성해야 적용이된다.
 7-2. DDL, DCL : 하나의 트랜잭션으로 DML과 달리 실행이 성공적으로 완료되면 바로 Commit된다.
 
