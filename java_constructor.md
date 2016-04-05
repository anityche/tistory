
기본기가 부족함을 느끼고 있다. 다시 한 번 차근 차근 복습도 할겸 알송달송한 부분들을 정리한다.

- [자바 프로그래밍언어(위키)](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4) "자바 프로그래밍언어")

>기초적인 부분이기도 하지만 모든 부분을 설명하지는 못하기에 어디까지나 개인적인 정리임을 감안하고 봐주길.


#### 생성자 

모든 클래스는 생성자라는 메소드와 비슷한 멤버를 가진다고 하는데 몇 가지 특성이 있다. 

- 리턴타입이 없다.
- 클래스 명과 동일한 명을 가진다.
- 명시적 선언을 하지 않아도 컴파일시 자동으로 만들어진다.
- 명시적 선언을 한다면 컴파일시 자동으로 만들어지지 않는다.
- 인수를 가질 수 있다.
- 메소드와 마찬가지로 오버로딩이 가능하다.

일반적으로 알고들 있는 내용인데(거짓말!) 기본 생성자 이외에 반드시 초기값이 선언되어야 할드 필드가 있다면 
사용시 오버로딩 하면서 `this` 키워드를 이용하여 좀 더 간략한 
코드를 만들 수 있다. 

```java
public class Car {
    String name;
    int number;

    public Car(){
        this("", 0);
    }
    public Car(String name) {
        this(name, 0);
    }
    public Car(int number) {
        this("", number);
    }
    public Car(String name, int number) {
        this.name = name;
        this.number = number;
    }
}
```

그럼 기본적으로 컴파일시 