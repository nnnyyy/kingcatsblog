---
title: 비전공 직군을 위한 자바스크립트 강좌 - 3. 조건문
date: 2018-12-29 11:46:28
tags:
- 자바
- Java
- 프로그래밍
- 조건문
- if
categories:
- 프로그래밍
- Java
---

> 이 강좌는 철저히 비전공 직군에게 최대한 쉽게 프로그래밍을 이해시키기 위해 만들었습니다.
> 전공자들에겐 다소 쉽고 지루할 수 있음을 미리 경고합니다.

***

# 잡담

갑자기 이런 생각이 든다.

'1,2강을 못 따라오면 어떻게 하지?... 그럼 이 강좌는 실패인데...'

.
.
.

근데 실제로 잘 따라오고 있는지 알 방법이 없기에 

주변 비개발직군 지인들에게 이 강좌를 보여줘서 따라올 수 있나 테스트를 좀 해봐야겠다. 

그래서 그 피드백을 받아서 수정 작업을 거쳐야지.

어쨌든 오늘은 `조건문` 배울 시간이다.

# 조건의 필요

이전 강좌의 코드를 다시 가져와보자.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        System.out.println("나의 hp : ");
        System.out.println(hp);
        // main의 영역 끝
     }
}
```

위 코드는 그냥 나의 hp 값을 출력 해주고 끝나는 프로그램이다.

여기서 나는 hp의 값에 따라서 "아직 살아있다", "죽었다" 등의 문자열을 출력해주고 싶다.

일단은 "죽었다" 를 출력해보자

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        System.out.println("나의 hp : ");
        System.out.println(hp);

        System.out.println("죽었다");
        // main의 영역 끝
     }
}
```

결과는

```
나의 hp :
20
죽었다
```

음 이쯤에서 저 거슬리는 줄바꿈부터 없애고 다시 시작하자.

> System.out.println("나의 hp : ");

를

> System.out.print("나의 hp : ");

으로 수정해보자

```
나의 hp : 20
죽었다
```
이제 좀 정리가 된 것 같다. `println` 대신 `print` 를 쓰면 줄바꿈을 하지 않는 다는 사실을 이제는 알아두자.

자 다시 본론으로 돌아와서

나는 hp가 20이 남아있는데 죽었다가 표시 되는 것은 이상하다.

그래서 나는 hp가 0 일때**'만'** `"죽었다"` 를 출력하고 싶다는 `조건` 이 필요하다.

# 조건문의 문법

조건문을 쓸 때는 `if` 라는 `예약어`를 사용한다.

`예약어`란 변수명으로 사용하지 못하도록 자바에서 미리 `예약`한 명령어라는 뜻이다.

> if :  만약, 만약 ... 라면

이라는 영어 뜻에 따라 우리는 `만약 hp 가 0 이라면 죽었다 를 출력한다` 를 

코드로 표현 해 볼 것이다.

``` java
if( 조건식 ) {
    실행 할 코드
}
```

기본적인 문법은 위와 같다

저기에 우리가 표현하고 싶은 조건을 한글로 써보면

``` java
if( hp 가 0 과 같으면 ) {
    죽었다를 출력하라
}
```

가 될 것이다.

일단 우리는 `죽었다를 출력하라` 는 어떻게 표현해야 할 지 알고 있다.

해당 위치의 한글을 코드로 바꿔보자.

``` java
if( hp 가 0 과 같으면 ) {
    System.out.println("죽었다");
}
```

그럼 이제 남은 것은 `hp 가 0 과 같음` 를 코드로 표현하는 일이다.

# 비교연산자의 등장

hp 와 0 이 서로 같은지를 비교해야 한다.

학창시절의 수학시간을 되새겨보면

우리는 같음을 표현할 때 `=` 이 기호를 사용했다.

그.러.나.

프로그래밍 나라 언어에서는 `=` 이것은 더 이상 `같음`을 의미하지 않는다.

이 나라에서 `=` 은 변수에 값을 `대입`하는 `대입연산자` 일 뿐이다.

``` java
hp = 0 // hp와 0은 같다 의 뜻이 아니라 hp 에 0값을 '대입'한다 이다.
```

<u>절!대!로! `=` 이 연산자로 비교하는 일이 있어서는 안된다.</u>

그러면 `hp와 0이 같다` 라는 것은 어떻게 표현할까?

이제는 `비교연산자`가 등장할 차례이다.

| 비교연산자 | 의미                   |
|:-:|:-:|
| A == B     | A와 B가 같다           |
| A >= B     | A 가 B보다 크거나 같다 |
| A > B      | A 가 B보다 크다        |
| A <= B     | A 가 B보다 작거나 같다 |
| A < B      | A 가 B보다 작다        |

위 표를 토대로 `hp 가 0 과 같음` 을 표현해 보면

``` java
hp == 0
```
가 된다. `조건식`을 만든 것이다. 이제 이 조건식을 

``` java
if( hp 가 0 과 같으면 ) {
    System.out.println("죽었다");
}
```

여기에 넣어보자

``` java
if( hp == 0 ) {
    System.out.println("죽었다");
}
```

그러면 최종 코드는 

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        System.out.print("나의 hp : ");
        System.out.println(hp);

        if( hp == 0 ) {
            System.out.println("죽었다");
        }        
        // main의 영역 끝
     }
}
```

이 된다. 실행해보면 

```
나의 hp : 20
```

이렇게 출력이 되는데, hp = 20; 을 hp = 0; 으로 변경하고 다시 실행해보자.

```
나의 hp : 0
죽었다
```

오! 뭔가 이제 조건에 따라 출력을 할지 말지 결정할 수 있게 되었다!

# 그럼 살았을 때는?

이제 hp가 0이면 죽었다는 표현할 수 있다.

그런데.. 이상태에서 hp가 0이 아닌경우 "살아있다"를 표현 해주고 싶다.

이럴때는 이제 `else` 를 사용한다.

``` java
if( 조건식 ) {
    실행할 코드
}
else {
    if의 조건식에 해당되지 않을 경우 실행할 코드
}
```
매우 간단하다.

그럼 이제 hp가 0이 아닐 경우에는 살려보자.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        System.out.print("나의 hp : ");
        System.out.println(hp);

        if( hp == 0 ) {
            System.out.println("죽었다");
        }        
        else {
            System.out.println("살아있다");            
        }
        // main의 영역 끝
     }
}
```

그리고 다시 실행 해보자.

```
나의 hp : 20
살아있다
```

이제 hp 의 `조건` 에 따라서 `살아있다` 와 `죽었다` 를 표현 해 줄 수 있게 되었다!

이 `if`문을 사용할 수 있다는 건 매우 중요하다.

'레벨업을 하게되면 ...', '몬스터가 나를 때리면...', '내가 방에서 나가면...' 등의

처리를 할 수 있는 기반을 마련했기 때문이다.

# 마치며

이제는 완전 감이 없진 않으리라 생각한다. ( 물론 열심히 계속 따라 쳐보았다면 )

눈으로만 읽는 것은 아무 의미가 없다. 

계속 해봐야한다.

기타 연습도 레슨은 1시간이고 나머지는 다 내가 연습하는 시간이다.

연습 안하면 아무리 레슨을 들어도 결국 내 것이 되지 않는다.

그러니까 열심히 해야한다.

# 다음이야기

다음은 같은 코드를 반복할 수 있는 `반복문` 에 대해 써 보겠다.

사실 여기서부터가 지옥문 1차 관문이다.

설명해 줄 때는 그럴싸한데 응용하기 시작하면 어버버버 하는 구간이다.

정신줄 놓지 말고 열심히 연습하자