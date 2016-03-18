
기본기가 부족함을 느끼고 있다. 다시 한 번 차근 차근 복습도 할겸 알송달송한 부분들을 정리한다.

- [자바 프로그래밍언어(위키)](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4) "자바 프로그래밍언어")

>기초적인 부분이지만 모든 부분을 설명하고 있지는 않다. 어디까지나 개인적인 정리임을 감안하고 봐주길.


### 제어문 

대표적인 `if` 말고 `switch` 문을 종종 사용할 때가 있다. 당연스럽게 `break;` 를 명시하여 제어문 밖으로 빠져 나오도록 사용했는데 
브레이크 코드를 명시하지 않으면 적합하는 케이스의 다음에 오는 케이스에도 적합하다고 판단한다. 

즉, 적합하는 케이스를 그룹화 시켜서 브레이크 코드를 걸지 않고 다음과 같이 사용할 수 있겠다.


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


### 반복문(for each)

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

많이 사용하는 편은 아니어서 가끔 선언시 자바스크립트 형태로 선언해 놓을 때가 있다. 

```javascript
//javascript 에서의 for in
for (x in iArr) {
    ...
}
```

