### 오늘 공부내역
1. Ioc

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
1.Field Injection
2.Setter Based Injection
3.Contructor based Injection

1.Field Injection
```JAVA
@Service
public class StudentServiceImpl implements StudentService {

    @Autowired
    private CourseService courseService;

    @Override
    public void studentMethod() {
        courseService.courseMethod();
    }

}
```
2.Setter based Injection
```JAVA
@Service
public class StudentServiceImpl implements StudentService {

    private CourseService courseService;

    @Autowired
    public void setCourseService(CourseService courseService) {
        this.courseService = courseService;
    }

    @Override
    public void studentMethod() {
        courseService.courseMethod();
    }
}
```
3.Contructor based Injection
```JAVA
@Service
public class StudentServiceImpl implements StudentService {

    private final CourseService courseService;

    @Autowired
    public StudentServiceImpl(CourseService courseService) {
        this.courseService = courseService;
    }

    @Override
    public void studentMethod() {
        courseService.courseMethod();
    }
}
```
>위의 3가지 방법중 3번째 방법인 생성자 주입방식을 권장한다. 권장하는 이유는 아래의 참조 링크를 확인하기 바란다.
[참조] https://yaboong.github.io/spring/2019/08/29/why-field-injection-is-bad/
[참조] https://gmlwjd9405.github.io/2018/11/09/dependency-injection.html

#### 한 줄
>예전에 정리를 한적도 있고 한 내용들이다. Spring에 대해서 다시한번 공부하면서 감을 찾고자 강의를 보며 검색을 하며 정리하였다. 다시 Spring을 공부하며 까먹은 부분들이 있지만 좋아했던 Spring을 다시 공부한다는게 즐겁다.
