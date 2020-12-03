### 오늘 공부목록
1. Spring구조
2. AOP개념

#### Spring 구조
![99A523405B9E2C1510](https://user-images.githubusercontent.com/51444580/100963434-acb03780-3569-11eb-8baa-f52430b1d37d.png)<br/>

##### Spring Core
>Spring Core는 Spring Container을 의미합니다. core라는 말 그대로 Container는 Spring Framework의 핵심이며 그중 핵심은 Bean Factory Container입니다.  그 이유는 바로 Bean Factory는 IOC패턴을 적용하여 객체 구성 부터 의존성 처리까지 모든 일을 처리하는 역할을 하고 있기 때문입니다.

##### Spring Context
Spring context는 Spring Framework의 context 정보들을 제공하는 설정 파일입니다. Spring Context에는 JNDI, EJB, Validation, Scheduiling, Internaliztaion 등 엔터프라이즈 서비스들을 포함하고 있습니다.

##### Spring AOP
Spring AOP module은 Spring Framework에서 관점지향 프로그래밍을 할 수 있고 AOP를 적용 할수 있게 도와주는 Module입니다. 해당 AOP에 대한 내용은 위에서 설명 했기 때문에 넘어 가도록 하겠습니다.

##### Spring DAO
DAO란 Data Access Object의 약자로 Database Data에 접근하는 객체입니다. Spring JDBC DAO는 추상 레이어를 지원함으로써 코딩이나 예외처리 하는 부분을 간편화 시켜 일관된 방법으로 코드를 짤 수 있게 도와줍니다.

##### Spring ORM
ORM이란 Object relational mapping의 약자로 간단하게 객체와의 관계 설정을 하는 것입니다. Spring에서는 Ibatis, Hibernate, JDO 등 인기있는 객체 관계형 도구(OR도구)를 사용 할 수 있도록 지원합니다.

##### Spring Web
Spirng에서 Web context module은 Application module에 내장되어 있고 Web기반의 응용프로그램에 대한 Context를 제공하여 일반적인 Web Application 개발에 필요한 기본적인 기능을 지원합니다. 그로인해 Jakarta Structs 와의 통합을 지원하고 있습니다.

##### Spring MVC
Spring에서는 MVC에서는 Model2 구조로 Apllication을 만들 수 있도록 지원합니다. MVC (Model-View-Controller) 프레임 워크는 웹 응용 프로그램을 작성하기위한 완전한 기능을 갖춘 MVC를 구현합니다. MVC 프레임 워크는 전략 인터페이스를 통해 고급 구성 가능하며 JSP, Velocity, Tiles, iText 및 POI를 포함한 수많은 뷰 기술을 지원하고 있습니다.
