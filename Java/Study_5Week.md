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

2. 클래스 작성 규칙 
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
3. 접근지정자
