## 자바 입문 공부할 때 아리까리 한 것들

기본기가 부족함을 느끼고 있다. 다시 한 번 차근 차근 복습할겸 정리한다. 

- [JAVA](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4) "자바 프로그래밍언어")

>기초적인 부분이지만 모든 부분을 설명하고 있지는 않다. 어디까지나 개인적인 정리임을 감안하고 봐주길.

### 상수

- 상수는 수식에서 변하지 않는 값을 뜻 한다. (변하는 값 = 변수)
- 상수를 선언할 때 `final` 키워드를 붙인다.
- 일반적인 관례로 상수 선언은 *대문자*로 하며 단어와 단어 사이에 언더바`(_)`를 붙인다.

```java
    final double PI = 3.14159;
    final double OLE_PRICE = 1450;
```


### 연산자

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

기초 입문 시절에 사소한 궁금증을 자아냈던 부분이기도 하다. 그리고 또 다른 예로 비교, 논리 연산자에 대해서도 
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


### 비트 연산자

`&&` 논리 곱 또는 `||` 논리 합 연산자는 많이 사용하는 논리 연산자 중 대표적이라 할 수 있겠다.
하지만 생각해보면 *싱글* 논리(?) 연산자인 비트 연산자는 사용할 일도 많지 않고 잘 모르고 있기도 하다.

>비트 연산은 정확한 이해가 없기에 어정쩡하게 본문에 포함시킬 수 없어서 직접 찾아보시길 권장함. 

비트 연산시 피연산자에는 반드시 정수가 와야 한다고 설명한 곳도 있었고, 문자형 그리고 실수나 부울린형에서도 에러를 발생 시킨다고 
하는 곳도 있는데 부울린형에서도 정상적이었다. 궁금해서 테스트를 해보기는 했지만 구지 비트연산자를 논리 연산자로 사용할 필요는 
없다고 생각한다. 

또 다른 점으로는 논리 곱, 논리 합 연산으로 싱글 사용시 두가지 조건 이상이 올 때 첫번째 조건에 적합하지 않아도 나머지 조건까지 조회 한다는 것이다.


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

논리 연산에 더욱 싱글을 사용하지 않아야 할 이유가 있다면 연산 소비 비용이 많이 든다.


### 제어문 

switch 문을 종종 사용할 때가 있다. 당연스럽게 `break;` 를 명시하여 제어문 밖으로 빠져 나오도록 사용했는데 
브레이크 코드를 명시하지 않고 사용하는 방법도 있다. 


```java
    int val = 2;
    
    switch(val) {
        case 1:
            System.out.println("1");
            break;
        case 2:
            System.out.println("2");
        case 3:
            System.out.println("3");    // case 2: 조건에서 break; 를 명시하지 않았기에 출력됨.
            break;
        default:
            System.out.println("default");
            break;
    }
    
//  java7 이후부터 문자열에도 스위치문이 사용된다.
```

>java 7 버전 이후로는 문자열 또한 스위치문에 적용시킬 수 있다.

