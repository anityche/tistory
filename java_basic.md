
기본기가 부족함을 느끼고 있다. 다시 한 번 차근 차근 복습도 할겸 알송달송한 부분들을 정리한다.

- [자바 프로그래밍언어(위키)](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4) "자바 프로그래밍언어")

>기초적인 부분이기도 하지만 모든 부분을 설명하지는 못하기에 어디까지나 개인적인 정리임을 감안하고 봐주길.


#### 변수

변수는 크게 기본과 참조 타입으로 나뉘고 기본형을 제외한 모든 타입을 참조형 타입으로 볼 수 있다.
그리고 기본형 타입에는 논리(boolean), 문자(char), 정수(byte, short, int, long), 실수(float, double) 형으로 
나뉘어진다.

>기본 타입은 원시(primitive) 타입이라고 부르기도 한다.  


#### 상수

참조형으로 선언할 수 없다. 참조형은 `new` 키워드를 선언하여 객체를 인스턴스화 시키는 것.

- 상수는 수식에서 변하지 않는 값을 뜻 한다. (변하는 값 = 변수)
- 상수를 선언할 때 `final` 키워드를 붙인다.
- 일반적인 관례로 상수 선언은 *대문자*로 하며 단어와 단어 사이에 언더바`(_)`를 붙인다.

```java
final double PI = 3.14159;
final double OLE_PRICE = 1450;
```

>상수는 리터럴(literal) 값 이라고 부르기도 한다.


#### 연산자

연산시 가로 안의 식을 우선시 하고 그 안에서도 연산자에 따라 우선시 되는 연산자가 있다는 것은 대부분
알고 있지만 잘 사용하지 않게 되는 연산자나 뭐 기타 등등에 해당하는 부분을 알아본다.

```java
int a = 5;
int b = 10;
int c = 15;

//1번예시
System.out.println( ++a - 5 );
1

//2번예시
System.out.println( a++ - 5 );
0
//값 0 이 출력이 되었지만 출력 후 a + 1 를 실행하기 때문에 실제로 메모리에는 6 이라는 값이 저장 된다.
```

기본적으로 연산은 왼쪽에서 오른쪽으로 진행된다. 하지만 단항 연산의 경우 반대로 진행된다.
대입 연산의 경우에도 오른쪽에서 왼쪽이다. 응? 오른쪽에서 왼쪽인데 위 1번식은 `++a` 먼저 계산했는데?

연산자의 우선순위를 좀 더 알아보자면 **단항 > 산술 > 비교 > 논리 > 삼항 > 대입** 연산자 순 이다.

작은 궁금증을 자아냈던 부분이기도 하다. 그리고 또 다른 예로 비교, 논리 연산자에 대해서도 
문득 헷갈려 했었는데 연산 방향이 왼쪽에서 오른쪽임을 몰라서였기 때문이었다.

예를 들면,

```java
int a = 5;
int b = 10;
int c = 15;
int i = 13;

if (i > a && i < c) {
    System.out.println(true);
} else {
    System.out.println(false);
}
```

위와 같은 논리식이 있을 때 `i` 와 `a, c` 를 비교하는 논리식에서 당연히 왼쪽에서 오른쪽 순으로 `i` 값에 대한 비교인데
`a` 가 `i` 보다 작은걸 비교하는 건가..? 싶은 착각이 들 때가 있었다는 뜻이다.

이 밖에도 나머지 연산과 나누기 연산을 자주 사용하지 않아 종종 어? 할때가 있다. 
`%`는 나누기에 동그라미가 붙어서 나머지 값을, `/`는 수학 그대로 나누기의 몫을 구한다고 생각하자. 라고 멋대로 정했었다.


#### 비트 연산자

`&&` 논리 곱 또는 `||` 논리 합 연산자는 많이 사용하는 논리 연산자 중 대표적이라 할 수 있다.
하지만 생각해보면 *싱글* 논리(?) 연산자인 비트 연산자는 사용할 일도 많지 않고 잘 모르고 있기도 하다.

>비트 연산은 정확한 이해가 없기에 어정쩡하게 본문에 포함시킬 수 없어서 직접 찾아보시길 권장함. 

비트 연산시 피연산자에는 반드시 정수가 와야 한다고 설명한 곳도 있었고, 문자형 그리고 실수나 부울린형에서도 에러를 발생 시킨다고 
하는 곳도 있는데 부울린형에서도 정상적이었다. 궁금해서 테스트를 해보기는 했지만 *구지 비트연산자를 논리 연산자로 사용할 필요는 
없다고 생각한다. *

또 다른 점으로는 논리 연산으로 싱글 사용시 두가지 조건 이상이 올 때 첫번째 조건에 적합하지 않아도 
나머지 조건까지 조회 한다는 것이다.


```java

static boolean retFalse() {
    System.out.println("call return false");
    return false;
}
static boolean retTrue() {
    System.out.println("call return true");
    return true;
}

public static void main(String[] args) {
    boolean result;
    
    // 더블 사용시 첫번째 조건에 적합하지 않다면 두번째 조건식까지 조회하지 않는다.
    result = ( retFalse() && retTrue() );   // 논리곱 
    System.out.println(result);
    
    result = ( retFalse() || retTrue() || retFalse() ); // 논리합 
    System.out.println(result);

    // 싱글 사용시 첫번째 조건에 적합하지 않아도 두번째 (이상) 조건식까지 조회한다.
    result = ( retFalse() & retTrue() );    // 논리합 
    System.out.println(result);
    
    result = ( retFalse() | retTrue() | retFalse() );   // 논리합 
    System.out.println(result);

}
```

논리 연산에 더욱 싱글을 사용하지 않아야 할 이유를 대라면 연산시 소비 비용이 많이 든다는 점?



#### 제어문 

대표적인 `if` 말고 `switch` 문을 종종 사용할 때가 있다. 당연스럽게 `break;` 를 명시하여 제어문 밖으로 빠져 나오도록 사용했는데 
브레이크 코드를 명시하지 않으면 적합하는 케이스의 다음에 오는 케이스에도 적합하다고 판단한다. 

즉, 적합하는 케이스를 그룹화 시켜서 브레이크 코드를 걸지 않고 다음과 같이 사용할 수 있다.


```java
int month = Calendar.getInstance().get(Calendar.MONTH) + 1;
String season = "";

switch (month) {
  case 1: case 2: case 12:
    season = "겨울";
    break;
  case 3: case 4: case 5:
    season = "봄";
    break;
  case 6: case 7: case 8:
    season = "여름";
    break;
  case 9: case 10: case 11:
    season = "가을";
    break;
}

System.out.println("지금은 "+ month +"월이고, "+ season +"입니다.");

```

>정수 타입만 스위치문에 사용할 수 있어서 좀 불편하다고 생각했는데 java 7 버전 이후로는 문자열 또한 스위치문에 사용할 수 있다.


#### 반복문(for each)

jdk 1.5 버전 이상 부터 향상된 for 라는 내용으로 기존의 포문 보다 간소화 된 선언으로 사용할 수 있는 루프문이다.
초기화가 없기에 scope 안에서의 제어가 불편하기도 하지만, 불가능한 것은 아니기에 단순 루프를 목적으로 한다면 매우 편리하다고 생각한다.

```java
int[] iArr = {1, 2, 3, 4, 5};

for (int i = 0; i < iArr.length; i++) {
    ...
}

for (int value : iArr) {
    ...
}
```

많이 사용하는 편은 아니어서 가끔 선언시 자바스크립트 형태로 선언해 놓을 때가 있다. 애용해야지..

```javascript
//javascript 에서의 for in
for (x in iArr) {
    ...
}
```

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


#### 오토박싱

기본 타입 데이터를 객체 타입의 데이터로 자동 형변환 시켜주는 기능.

```java
int i = 5;  //기본타입
Integer i2 = new Integer(5);    //객체 타입 (본래 인스턴스화 시켜서 사용했으나 아래와 같이 사용할 수 있음)

Integer i3 = 5; //오토박싱 (자동 형변환)
//실제 컴파일시 new Integer(5); 라고 자동으로 변환한다.

int i4 = i3.intValue();
int i5 = i3;    //오토언박싱 
```

> JAVA 1.5 이후 부터 가능

- [Integer Class](https://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html "Integer")


#### 반복문 안에서의 String 연산

```java
String str = "";
for (int i=0; i < 1000; i++) {
    str = str + "*";
}
//위와 같은 String `+` 연산 코드는 실제로 컴파일시 String 객체를 1000번 생성한다. (성능 다운)

StringBuffer sb = new StringBuffer();
for (int i=0; i < 1000; i++) {
    sb.append("*");
}
//그래서 위와 같은 메소드체이닝 방식을 사용하는 StringBuffer 클래스를 이용하는 것이 좋다.
```

>method chaining - 자신을 리턴하며 메소드를 이어가는.. `sb.append().append().append().toString()`


#### 필수 패키지

자바에서 가장 기본이자, 가장 많이 사용 되는 패키지

- java.lang
- java.util
