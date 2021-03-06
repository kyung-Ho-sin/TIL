### 오늘 공부목록 및 하루 일과
1. DB Inner Join Outer Join
2. 오후 2시 면접

#### DB Inner Join이란?
>내부조인(Inner Join)은 등가조인 및 단순조인 이라고도 한다. 테이블을 연결한 후에 출력 행을 각 테이블의 특정 열에 일치한 데이터를 기준으로 선정하는 방식이다.

 ```
 SELECT 컬럼명 FROM 테이블A, 테이블B WHERE 테이블A.컬럼명 = 테이블B.컬럼명 
 ```
 >여러 테이블을 JOIN할때의 유의할점이 있다. 같은 컬럼명이 있을때를 조심해야 한다. 컬럼명이 같다면
 ```
 [Error]Execution: ORA-00918: 열의 정이가 애매합니다.
 ```
>이와 같은 오류가 발생할수 있다. 해당 오류를 피하기 위해선 어느 테이블에 존재하는 컬럼인지를 명확하게 해주는것이 중요하다.

#### DB Outer Join이란?
>EQUI JOIN(내부조인, 등가조인)은 조인하는 두 테이블의 공통된 값이 없다면 값이 나오지 않는다는 점이다. 해당 부분을 보완하기 위한 조인이 아우터 조인이다. OUTER JOIN의 연산자는 (+) 이다. 해당 (+) 연산자를 붙이는 방향은 데이터가 없을 수도 있는 쪽 컬럼에 추가하여 사용한다.
```
SELECT 컬럼명1, 컬럼명2, 컬럼명3, 컬럼명4 FROM 테이블A, 테이블 B 
WHERE 테이블A.컬럼명 = 테이블B.컬럼명
AND 테이블A.컬럼명 = 테이블B.컬럼명(+)
```
>조인을 하는 대상 테이블의 값이 없을수도 있는 부분에 + 연사자를 사용하여 값이 나올수 있게 한다.

### 면접 준비 기록 (1부)
자바 CS 문제
>1.JVM 이란?
- JVM은 Java와 OS사이에서 중개자 역할을 수행하여 Java와 OS에 구해받지 않고 재사용을 가능하게 해줍니다. JVM은 스택기반으로 동작합니다.

>2.Collection의 종류 <br/>
  ##### List, Map, Set <br/>
  - Map은 key value 의 구조로 이루어져있으며 수집의 순서를 기억하지 않고 동일한 데이터를 Key값으로 사용할 수 없다.
  - List는 수집의 순서가 있으며 동일한 데이터의 중복 입력이 가능하다. 순차적으로 대량의 데이터를 엑세스하거나 입력할 때 유리하다
  - Set은 중복데이터를 불허하는 것을 제외하고는 큰 특징이 없다. 입력되는 당시의 순서에는 따르지 않으나 순차적인 접근을 위해서는 iterator로 접근하게 된다.<br/>
  ##### Map 과 list의 차이점<br/>
   - ArrayList의 경우 단순히 데이터를 입력하고 데이터를 출력하는 용도로 HashMap의 경우 데이터를 캐쉬해서 특정 Key값으로 HashMap에 있는 데이터를 검색해서 사용하는 용도로 사용 <br/>
  ##### Collection의 사용이유 <br/>
   - 다수의 Data를 다루는데 표준화된 클래스들을 제공해주기 때문에 DataStructure를 직접 구현하지 않고 편하게 사용할 수 있기 때문이다. <br/>
  ##### Stack 과 Queue <br/>
   - Stack은 후입선출 : LIFO(List in First out) 구조이다 / 같은 구조와 크기의 자료를 정해진 방향으로만 쌓을수 있으며 top으로 정한 곳을 통해서만 접근이 가능 / 스택에 아무것도 없는데 뺄려고 할때 스택언더플로우 / 넘치는 경우 스택오버플로우
   - Queue는 선입선출 : FIFO(First in First out) 구조이다 / 삭제연산만 수행되는곳을 프론트 / 삽입연산만 이루어지는곳을 리어 라고 한다.

>3.Annotation <br/>
   - 본래 주석이란 뜻으로, 인터페이스를 기반으로 한 문법이다. 주석과는 그 역할이 다르지만 주석처럼 코드에 달아 클래스에 특별한 의미      를 부여하거나 기능을 주입할 수있습니다. / 총 3가지 built-in anno / meta anno / Custom anno / Override 는 built

>4.Generic <br/>
   - 다양한 타입의 객체들을 다루는 메서드나 컬렉션 클래스에서 타입을 체크해주는 기능입니다.

>5.Overriding 과 Overloading <br/>
   - 오버라이딩은 상위 클래스에 존재하는 메소드를 하위 클래스에서 필요에 맞게 재정의하는 것을 의미한다.
   - 오버로딩은 상위 클래스의 메소드와 이름, return 값은 동일하지만, 매개변수만 다른 메소드를 만드는 것을 의미한다. 다양한 상황에      서 메소드가 호출될 수 있도록 한다.

>6. 접근제어자 <br/>
  - public : 어떤 클래스에서라도 접근이 가능하다.
  - protected : 클래스가 정의되어 있는 해당 패키지 내 그리고 해당 클래스를 상속받은 외부 패키지의 클래스에서 접근이 가능하다.
  - default : 클래스가 정의되어 있는 해당 패키지 내에서만 접근이 가능하도록 접근 범위를 제한한다.
  - private : 정의된 해당 클래스에서만 접근이 가능하도록 접근 범위를 제한한다

개발 상식 <br/>
>1. 객체 지향 프로그래밍이란 무엇인가? <br/>
 - 기능들을 여러 개의 객체 단위로 나눠 작업하는 방식을 말합니다. / 즉 독립된 객체 들의 모임이라 생각합니다. <br/>
 ##### 추상화 <br/>
 - 대상의 특성 중 불필요한 부분을 무시하고 공통점만 다루어 현실의 복잡성을 극복하고 목적에 집중할 수 있도록 하는 것 <br/>
 ##### 캡슐화 <br/>
 - 데이터를 외부에서 접근하는 것을 방지하고 오로지 함수를 통해서만 접근할 수 있게 하는 것 <br/>
 ##### 상속성 <br/>
 - 부모 클래스의 속성과 기능을 상속받아 동일하게 사용하는 것 <br/>
 ##### 다형성 <br/>
 - 동일 요청에 대해 서로 다른 방식으로 응답할 수 있도록 만드는 것 <br/>

>2. 객체 지향적 설계 원칙 <br/>
 ##### SRP(Single Responsibility Principle) : 단일 책임 원칙 <br/>
 - 클래스는 단 하나의 책임을 가져야 하며 클래스를 변경하는 이유는 단 하나의 이유이어야 한다. <br/>
 ##### OCP(Open-Closed Principle) : 개방-폐쇄 원칙 <br/>
 - 확장에는 열려 있어야 하고 변경에는 닫혀 있어야 한다. <br/>
 ##### LSP(Liskov Substitution Principle) : 리스코프 치환 원칙 <br/>
 - 상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상적으로 동작해야 한다. <br/>
 ##### ISP(Interface Segregation Principle) : 인터페이스 분리 원칙 <br/>
 - 인터페이스는 그 인터페이스를 사용하는 클라이언트를 기준으로 분리해야 한다. <br/>
 ##### DIP(Dependency Inversion Principle) : 의존 역전 원칙 <br/>
 - 고수준 모듈은 저수준 모듈의 구현에 의존해서는 안된다. <br/>
>3.Rest의 구체적인 개념 <br/>
 - HTTP URI 를 통해 자원을 명시하고, HTTP Method(Post, Get, Put, Delete)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.<br/>
 ##### 장점<br/>
 - HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.<br/>
 ##### 단점<br/>
 - 사용할 수 있는 메소드가 4가지 밖에 없다.<br/>
>4.Rest API란?<br/>
 - Rest 기반으로 서비스 API를 구현한 것<br/>
 ##### API란?<br/>
 - 데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간 상호작용을 촉진하며, 서로 정보를 교환가능 하도록 하는 것<br/><br/>
>5.Restful 이란?<br/>
 - Rest라는 아키텍쳐를 구현하는 웹 서비스를 나타내기 위해 사용되는 용어이다. Rest api를 제공하는 웹 서비스를 Restful하다고 할수 있다.<br/>

>6.TDD란?<br/>
 - 매우 짧은 개발 사이클의 반복에 의존하는 소프트웨어 개발 프로세스이다. 기능에 대한 자동화된 테스트케이스를 작성하고 해당 테스트 를 통과하는 간단한 코드를 작성해 리팩토링하는 과정입니다.<br/>

>7. Array 와 Linked List<br/>
 ##### Array<br/>
  - 인덱스로 해당 원소에 접근할 수있다. 그렇기 대문에 찾고자 하는 원소의 인덱스 값을 알고 있으면 Big-O(1)의 시간이 걸린다.<br/>
  - 하지만 Array안에 원소를 삭제할시 모든 값을을 Shift해줘야 하기 때문에 O(n)의 시간이 걸린다.<br/>
  
#### 조인 공부 느낀점
>Outer Join  과 Inner Join를 정확하게 사용하는 방법과 왜 사용하는지에 대해 완벽하게 이해하고 응용할수 있게 되었다. 오늘 면접에서 DB가 약하다고 느껴지는 순간이 있었다. 좀더 DB에 대해서 공부하고 이해하는 방향으로 진행해야할듯하다.

