
- [POJO(Plain Old Java Object)](https://ko.wikipedia.org/wiki/Plain_Old_Java_Object)

구지 의미를 생각하지 말자. 처음에 뭔가 했는데 그냥 객체다. 부모(종속된 상위) 객체가 많지 않은 그냥 가벼운 객체 정도 쯤?
>스프링 프레임워크 개발자 왈 "...적당한 이름을 하나 만들어 붙였더니, 아 글쎄, 다들 좋아하더라고.."


## IoC(Inversion of Control)와 DI(Dependency Injection)

처음에 개념을 잡기 위해 *IoC*와 *DI*라는 것에 대한 내용을 읽다 보니 좀 처럼 머리속에 들어오지 않았다.
*제어의 역전*과 *의존성 주입*이 명확하게 구분이 되어 있지 않고 그게 그거 아닌가? 싶더라.



간단하게 IoC Container는 Bean(=객체=클래스) 들을 관리해주는 박스라고 생각하자. 이 컨테이너에 선언된 
Metadata에 의해 관리 된다. 

`*context.xml` 파일에 선언되어

IoC가 DI 인가? 생각이 들었는데 


- [마틴파울러 글 번역본 자바캔 블로그](http://javacan.tistory.com/entry/120) 참고


AOP(Aspect Oriented Programming)

