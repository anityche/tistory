
기본기가 부족함을 느끼고 있다. 다시 한 번 차근 차근 복습도 할겸 알송달송한 부분들을 정리한다.

- [자바 프로그래밍언어(위키)](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4) "자바 프로그래밍언어")

>기초적인 부분이기도 하지만 모든 부분을 설명하지는 못하기에 어디까지나 개인적인 정리임을 감안하고 봐주길.  


### String Class

- 예외적으로 기본형과 참조형 타입의 특성을 모두 가지고 있다고 볼 수 있다.
- 기본형, 참조형 타입의 선언 두 가지의 방법으로 선언이 가능하다. 
- 한번 생성되면 생성된 인스턴스의 값이 변하지 않는다.

```java
public static void main(String[] args) {
    String str1 = "hello";      // 기본형 타입으로 선언시 상수영역에 생성됨
    String str2 = "hello";      // str2 생성시 "hello" 라는 값을 가진 상수영역의 String 인스턴스를 검색하여 str1 의 주소 값을 참조함
    
    String str3 = new String("hello");      // new 선언시 상수영역을 참조하지 않고 새로운 인스턴스를 힙 영역에 생성함
    String str4 = new String("hello");      // new 선언으로 또 다시 새로운 인스턴스를 힙 영역에 생성함
    
    System.out.println("------------------------------------ == 비교 (인스턴스의 주소(레퍼런스)를 비교함)");
    
    if (str1 == str2) {  // 같은 인스턴스를 참조하므로 결과는 true 
        System.out.println("str1과 str2는 같은 레퍼런스입니다.");
    }
    if (str1 == str3) {  // str1과 str3은 서로 다른 인스턴스를 참조하므로 결과는 false 
        System.out.println("str1과 str3는 같은 레퍼런스입니다.");
    }
    if (str3 == str4) {  // str3과 str4는 서로 다른 인스턴스를 참조하므로 결과는 false 
        System.out.println("str3과 str4는 같은 레퍼런스입니다.");
    }
    
    System.out.println("------------------------------------ equals() 비교 (인스턴스의 값을 비교함)");
    
    if (str1.equals(str2)) {
        System.out.println("str1과 str2는 같은 값 입니다.");
    }
    if (str1.equals(str3)) { 
        System.out.println("str1과 str3는 같은 값 입니다.");
    }
    if (str3.equals(str4)) { 
        System.out.println("str3과 str4는 같은 값 입니다.");
    }
    
    System.out.println("---------------------------------- ");
    
    //String 은 한번 생성되면 내부의 값이 변하지 않는다. (새로 생성한 인스턴스의 값을 돌려줌)
    System.out.println(str1.substring(3));  // str1 의 값을 수정함
    System.out.println(str1);       //  str1 의 값은 변하지 않았음
    
}
```

String Class 에 대해서 심도 있게 공부를 하면 꽤 많은 분량이 나올 것 같다. 왜 냐면.. 나도 잘 모르니까.



#### equals(), hashcode() method

종종 개발자들이 설계한 클래스를 보다 보면 `equals()`와 `hashcode()`는 **override** 해서 사용하는 것을 
보게 되는데 왜 그럴까? 어디서는 반드시 오버라이드 하여 사용할 것을 명시한다. 왜 그럴까? 뭔가 버그가 있으니 
그렇다는 건 알겠는데...

그래서 직접 스스로 해본다.

스트링 클래스에서 `equals()`는 값을 비교한다고 했다. 자세히는 생성된 인스턴스의 *참조 값*을 비교한다고 한다. 
음.. 참조 값... 여기서 중요한 부분은 **생성된 인스턴스의 참조 값** 이라는 부분일까?

나는 스트링 필드를 갖는 클래스를 하나 생성하고 인스턴스를 생성했다. 그리고 인스턴스의 내부 값을 비교하려고 
`equals()` 를 사용했다. 그런데 값이 다르다. 왜 일까?


```java
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}
```


ㅁㄴㅇㄻㄴㅇㄹ



```java
public static void main(String[] args) {
    MyStrClass mc1 = new MyStrClass("hello");
    MyStrClass mc2 = new MyStrClass("hello");
    
    if (mc1.equals(mc2)) {
        System.out.println("mc1, mc2 같은 값 입니다.");
    } else {
        System.out.println("mc1, mc2 다른 값 입니다.");
    }
    
    System.out.println(mc1.hashCode());
    System.out.println(mc2.hashCode());
    System.out.println("-------------------------------");
    
    MyStrClass mc3 = mc1;
    MyStrClass mc4 = mc3;
    
    if (mc3.equals(mc4)) {
        System.out.println("mc3, mc4 같은 값 입니다.");
    } else {
        System.out.println("mc3, mc4 다른 값 입니다.");
    }
    
    System.out.println(mc1.hashCode());
    System.out.println(mc2.hashCode());
    System.out.println(mc3.hashCode());
    System.out.println(mc4.hashCode());
}
```

분명 `equals()` 는 

String Class 의 equals method 를 살펴보면 다음과 같은데,

```java
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}
```






정석처럼 스트링 클래스의 메소드 중 `equals()` 를 오버라이드 해서 사용하는 코드를 보게 된다. 하지만 정작 
왜 오버라이드를 해야 하는지, 그리고 왜 `hashcode()` 메소드와 같이 오버라이드 하는지 알송달송 하다.


#### String Class - hashcode method



