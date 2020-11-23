### 오늘 공부목록
1. Session
2. Lock

#### Session
1.오라클 사용자가 데이터베이스에 접속하면 세션이 생성된다. 세션은 사용자가 데이터베이스에 연결되어 있는 동안 계속 유지되고 각 세션에는 SID와 시리얼 번호가 부여된다.
2.SID와 시리얼번호가 두개 존재하는 이유는 세션이 종료되었으나 사른 세션이 동일한 SID를 갖고 시작되었을 때 세션 명령들이 정확한 세션에 적용될 수 있도록 하기 위해서이다.

##### 세션 상태 확인
```
SHOW PARAMETER SESSIONS
```
>기본적으로 오라클 db에 최대 sESSION으로 젹용되어있는 것을 확인할수 있는 쿼리이다.

```
SELECT USERNAME, PROGRAM FROM V$SESSION;
```
>어떤 사용자들이 DB에 접속하였고 어떤 프로그램을 수행하고 있는지 확인하는 쿼리이다.

##### 세션 강제 종료
```
SELECT USERNAME, SID, SEIAL#, STATUS FROM V$SESSION WHERE USERNAME = 'SUNNY'

USERNAME                SID         SERIAL#       STATUS
--------------------- -------------- -------------- ----------------
SUNNY                       10               3             INACTIVE
```
```
ALTER SYSTEM KILL SESSION '10, 3';

SELECT USERNAME, SID, SEIAL#, STATUS FROM V$SESSION WHERE USERNAME = 'SUNNY'

USERNAME                SID         SERIAL#       STATUS
--------------------- -------------- -------------- ----------------
SUNNY                       10               3              KILLED
```
>오라클이 세션을 강제 종료할 떄, 해당 세션은 더 이상의 SQL문을 실행하는 것을 막는다. 만일 강제 종료하는 시점에 SQL문을 실행 중이었다면, 해당 SQL문은 종료되고 모든 변경사항들은 롤백된다. 또한 해당 세션에 의해 사용되던 잠금(LOCK) 및 기타 자원들도 해제된다.

### LOCK
>특정세션에서 조작중인 데이터는 트랜잭션이 완료(COMMIT, ROLLBACK)되기 전까지 다른 세션에서 조작할 수 없는 상태가 됩니다.즉 데이터가 잠기는 것이다. LOCK은 조작 중인 데이터를 다른 세션은 조작할 수 없도록 접근을 보륫 시키는 것을 뜻한다.
```
SELECT  DO.OBJECT_NAME, DO.OWNER, DO.OBJECT_TYPE, DO.OWNER,
        VO.XIDUSN, VO.SESSION_ID, VO.LOCKED_MODE
FROM    V$LOCKED_OBJECT VO, DBA_OBJECTS DO
WHERE   VO.OBJECT_ID = DO.OBJECT_ID;
```
>LOCK이 걸린 테이블을 확인하는 쿼리문이다.

```
SELECT DISTINCT t1.session_id AS session_id
               ,t2.serial# AS serial_no
               ,t1.os_user_name AS os_user_name
               ,t1.oracle_username AS oracle_username
               ,t2.status AS status
               ,t3.object_name
               ,DECODE( locked_mode
                       ,2, 'ROW SHARE'
                       ,3, 'ROW EXCLUSIVE'
                       ,4, 'SHARE'
                       ,5, 'SHARE ROW EXCLUSIVE'
                       ,6, 'EXCLUSIVE'
                       ,'UNKNOWN'
                      ) lock_mode
           FROM v$locked_object t1, v$session t2, dba_objects t3
          WHERE t1.session_id = t2.SID
            AND t1.object_id = t3.object_id;
       
alter system kill session '*SESSION_ID*,*SERIAL_NO*';
```
>락이 걸린 시리얼 넘버와 아이디 를 검색한후 KILL하는 쿼리문이다.

### 한 줄
>LOCK 부분이 진짜 어려운듯하다. 그냥 LOCK이란 개념을 이해하는것은 어렵지 않으나 상황에 따른 쿼리문을 작성하고 KILL하는 부분이 어려운듯하다.

