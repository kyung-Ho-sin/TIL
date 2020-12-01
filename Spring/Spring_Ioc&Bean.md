### 오늘 공부내역
1. Ioc
2. Bean

#### Ioc(Inversion of Control)
>제어의 역전이라 불리며 Bean들의 의존관계의 제어를 직접해 주었지만 제어권이 컨테이너로 넘어가고 객체의 생성부터 생명주기의 관리까지 역전 된것을 IOC라고 한다.

*IOC 컨테이너란?
- 애플리케이션 컴포넌트의 중앙 저장소
- 빈 설정 소스로 부터 빈 정의를 읽어들이고, 빈을 구성하고 제공한다.
- 객체들의 전체 수명주를 관리한다.
```JAVA
@Repository
public class BookService{
  private BookRepository bookRepository = new BookRepository();
}
```
>위 코드는 객체를 생성하여 사용한다. 저렇게 객체를 생성하면 BookService는 BokkRepository와의 의존관계가 생성된다.
```JAVA
@Repository
public class BookService{
  BookRepository bookRepository;
  
  @Autowired
  public BookService(BookRepository bookRepository){
    this.bookRepository = bookRepository;
  }
}
```
>생성자를 통해서 객체에 주입을 한다. 객체 주입이란 말이 나와 DI란 것에 대해 설명을 한 후 넘어가겠다.

#### Dependency Injection(의존관계 주입)
>객체 자체가 아니라 Framework에 의해 객체의 의존성이 주입되는 설계 패턴이다.

*의존관계 주입(Dependency Injection)종류
1.Setter Based Injection
2.Contructor based Injection


[참조] https://gmlwjd9405.github.io/2018/11/09/dependency-injection.html
