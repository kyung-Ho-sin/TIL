### 5주차 학습내용
1. 클래스 정의하는 방법
2. 객체 만드는 방법 (new 키워드 이해하기)
3. 메소드 정의하는 방법
4. 생성자 정의하는 방법
5. this 키워드 이해하기 

#### 클래스 정의하는 방법
1. 클래스
- 클래스는 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메소드(method)로 구성된다.
- 객체를 생성하기 위한 틀이다.
- 자바는 클래스들의 모임으로 이루어져 있다.

2. 클래스의 구성 멤버
- 필드 : 클래스 안에서 선언되는 멤버 변수
- 생성자 : 객체 생성시 인스턴스 변수를 원하는 값으로 초기화할 수 있게 도와주는 메소드
- 메소드 : 특정 작업을 수행하기 위한 명령문의 집합
```JAVA
public class Class {
	//필드
	//멤버 변수
	String Today;
	String Week;
	//클래스 변수
	static String name;
	
	//생성자 생성시 생략 가능 
	public Class() {}
	//파라미터가 있을시는 생성해야한다
	public Class(String Today, String Week) {
		this.Today = Today;
		this.Week = Week;
	}
	//메소드
	public void Method() {
		
	}
}
```
3. 클래스 작성 규칙 
- 하나 이상의 문자로 이루어져야 한다. 
- 첫 번째 글자에는 숫자가 올 수 없다. 
- $,_ 외에는 특수문자 사용불가 하다.
- 자바 명령어, 키워드는 사용할 수 없다.
```JAVA
// 가능
public class _Class {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
	}
}
// 불가능
public class @Class {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
	}
}
```
4. 접근지정자 <br/>
![접근지정자](https://user-images.githubusercontent.com/51444580/102589042-c482e080-4151-11eb-9569-f76f9782624d.GIF) <br/>
- public : 모든 접근을 허용
- protected : 상속받은 클래스 또는 같은 패키지에서만 접근가능
- default : 자신 클래스 내부와 같은 패키지 내에서만 접근 가능
- private : 외부 접근 불가 같은 클래스 내에서만 접근이 가능

#### 객체 만드는 방법(new 키워드 이해하기)
클래스를 사용하기 위해서 객체로 만들어 사용해야한다. 이렇게 클래스로부터 객체를 선언하는 과정을 인스턴스 화라고 한다.
이렇게 선언된 클래스 타입의 객체를 인스턴스 라고 한다.</br>
*인스턴스란 메모리에 할당된 객체를 의미한다.
```
클래스명 변수명
변수명 = new 클래스명();
Car car;
car = new Car();
```

#### 메소드 정의하는 방법
1. 메소드
- 특정 작업을 수행하기 위한 명령문의 집합
- 중복되는 코드의 프로그래밍을 피할수 있기 때문에 사용 (가독성 향상, 유지보수 용이)
```JAVA
접근제어자 반환타입 메소드이름(매개변수목록) { // 선언부
    // 구현부
}

public String Method(String name){
	System.out.println(name);
}
```
- 접근 제어자 : 메소드의 접근 범위
- 반환 타입 : 반환하는 데이터의 타입을 명시
- 매개변수 : 메소드 호출 시에 전달되는 인수의 값을 저장할 변수들을 명시
- 구현부 : 메소드의 기능을 수행하는 명령문의 집합
2. 메소드 오버로딩
- 같은 이름의 메소드를 중복하여 정의하는 것을 의미한다.
- 같은 이름으로 메소드를 정의할때는 매개변수의 개수나 타입을 다르게 하면 정의 할수있다.
- 메소드 오버로딩은 객체 지향 프로그래밍의 특징 중 하나인 다형성을 구현하는 방법중 하나이다.
```JAVA
public void Method() {
	System.out.println();
}
	
public void Method(String Test) {
	System.out.println();
}
```
#### 생성자 정의하는 방법
1. 생성자
- 객체를 생성할 때 항상 실행되는 것으로, 객체를 초기화해주기 위해 맨 처음 실행되는 메소드이다.
- 반환값이 없다.
- 클래스에는 반드시 생성자가 존재해야 한다.(생서자를 안만들시 default로 생성된다)
- 인스턴스 생성시 딱 한번 호출 된다.
- 인스턴스 변수의 초기화가 목적이다.
- 클래스 이름과 동일한 이름을 가진다.
```JAVA
public Class(String Today, String Week) {
	this.Today = Today;
	this.Week = Week;
}

public static void main(String[] args) {
	// 오류
	Class cls = new Class();
	// 동작
	Class cls = new Class("이름","5주차");	
}
```
#### this 키워드 이해하기
- 현재 클래스의 인스턴스를 의미한다.
- 현재 클래스의 멤버변수를 지정할때 사용한다.
- this 와 this()는 다르다.
```JAVA
public class Class {
	
	String name;
	String age;
	
	public Class() {
		this.name = "name";
		this.age = "age";
	}
	
	public Class(String name, String age) {
		this.name = name;
		this.age = age;
	}
}
```
