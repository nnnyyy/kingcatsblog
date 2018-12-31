---
title: 비전공 직군을 위한 자바스크립트 강좌 - 4. 반복문
date: 2018-12-30 07:56:15
tags:
- 자바
- Java
- 프로그래밍
- 반복문
- for
categories:
- 프로그래밍
- Java
---

> 이 강좌는 철저히 비전공 직군에게 최대한 쉽게 프로그래밍을 이해시키기 위해 만들었습니다.
> 전공자들에겐 다소 쉽고 지루할 수 있음을 미리 경고합니다.

***

# 잡담

회사 비개발 직군 2명에게 최근 `반복문`을 가르쳤다.

역시 설명하면 기초는 따라했지만 조금만 응용 해 버리면 막혀버리고 만다.

당연한 이야기다.. 

진짜 제대로 전공자들처럼 능숙하게 해보고 싶으면

결국 전공자들이 노력했던 시간만큼은 노력을 해줘야 한다.

이제부턴 죽어라 `반복`이다

---

# 비슷한 행동의 반복

[이전 강좌](/2018/12/29/JavaLecture3/) 에서 우리는 조건에 따른 분기 `if문`의 사용까지 배웠다.

if문의 문법을 다시 한번 보자.

``` java
if( 조건식 ) {
    실행할 코드
}
else {
    if의 조건식에 해당되지 않을 경우 실행할 코드
}
```

if문은 <u>조건식이 `참(true/ 사실)` 일 때 </u> 중괄호 영역(Block)에 있는 코드를 실행시킨다고 했다.

( 위에서는 `실행할 코드` 라고 쓰여있는 부분 )

이전 강좌 마지막까지 완성된 코드를 다시 불러와보자.

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

이것을 실행해보면 

```
나의 hp : 20
살아있다
```

를 출력했다.

여기서 갑자기 내가 살아있거나 죽어있음을 3번 알리고 싶어졌다.

이렇게 

```
나의 hp : 20
살아있다
나의 hp : 20
살아있다
나의 hp : 20
살아있다
```

어떻게 하겠는가? 

우리가 이제까지 배운 걸 토대로 만들어보자.

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

        System.out.print("나의 hp : ");
        System.out.println(hp);

        if( hp == 0 ) {
            System.out.println("죽었다");
        }        
        else {
            System.out.println("살아있다");            
        }

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

짠~

결과를 보면 확실히 원하는대로 잘 나온다.

그리고 알려줄 때마다 내가 몇번째로 알려줬는지도 같이 쓰고 싶다.

hp를 알려 줄 때마다 왼쪽에 숫자를 적어주자.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;

        System.out.print(1);
        System.out.print(".");
        System.out.print("나의 hp : ");
        System.out.println(hp);

        if( hp == 0 ) {
            System.out.println("죽었다");
        }        
        else {
            System.out.println("살아있다");            
        }

        System.out.print(2);
        System.out.print(".");
        System.out.print("나의 hp : ");
        System.out.println(hp);

        if( hp == 0 ) {
            System.out.println("죽었다");
        }        
        else {
            System.out.println("살아있다");            
        }

        System.out.print(3);
        System.out.print(".");
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

실행하면

```
1.나의 hp : 20
살아있다
2.나의 hp : 20
살아있다
3.나의 hp : 20
살아있다
```

좋다 여기까진 아주 깔끔하게 원하는 바를 해냈다

그런데 갑자기 생각이 바꼈다

내 생존여부를 100번을 알리고 싶어졌다

음...

.
.

지금까지 알고 있는 방법으로는 꽤나 

끔찍한 코드가 될 것 같은 느낌이 들기 시작한다.

정신차리고 반복이 되는 부분을 스마트하게 바꿀 시간이 온거다.

# 반복문의 등장

위 코드에서 반복적으로 나오는 비슷한 코드는 뭐 였는지 기억할 것이다.

``` java
System.out.print(1);
System.out.print(".");
System.out.print("나의 hp : ");
System.out.println(hp);

if( hp == 0 ) {
    System.out.println("죽었다");
}        
else {
    System.out.println("살아있다");            
}

System.out.print(2);
System.out.print(".");
System.out.print("나의 hp : ");
System.out.println(hp);

if( hp == 0 ) {
    System.out.println("죽었다");
}        
else {
    System.out.println("살아있다");            
}

System.out.print(3);
System.out.print(".");
System.out.print("나의 hp : ");
System.out.println(hp);

if( hp == 0 ) {
    System.out.println("죽었다");
}        
else {
    System.out.println("살아있다");            
}
```

1,2,3 이라는 숫자가 달라진 것을 제외하고는 3개 모두 동일하게 생긴 코드이다. 

정확히 아래 코드의 반복이다.

``` java
System.out.print(1씩 증가되는 숫자);
System.out.print(".");
System.out.print("나의 hp : ");
System.out.println(hp);

if( hp == 0 ) {
    System.out.println("죽었다");
}        
else {
    System.out.println("살아있다");            
}
```

이제 이 코드를 `반복문`을 써서 내가 원하는 횟수만큼 반복을 시켜 줄 것이다.

반복문의 문법은 다음과 같다.

``` java
for( 초기화 ; 조건식 ; 증감식 ) {
    반복할 코드
}
```

뭔가 새로운 것들이 갑자기 많이 등장해버렸다.

`for`는 무엇이고, `초기화`는 무엇이며, `증감식`은 또 무엇인가..

갑자기 겁부터나지만 그래도 하나씩 알아가보자.

# 반복문의 사용

`for`는 영어로 여러가지 뜻이 있지만 그중에

> for : ...동안 

이라는 뜻이 있다.

다시 for문의 문법을 보자.

``` java
for( 초기화 ; 조건식 ; 증감식 ) {
    반복할 코드
}
```

여기서 우리가 모르는 `초기화`와 `증감식`은 제외하고,

``` java
for( ; 조건식 ; ) {
    반복할 코드
}
```

이 상태에서 해석을 하면

> `조건식`이 `참`일 `동안(for)` <u>영역안에 있는 코드를 반복해라.</u>

라는 뜻이다. 

아까 위에서 반복적인 코드가 있었다.

이제는 그 코드를 반복문 안으로 모셔오자.


``` java
for( ; 조건식 ; ) {
    // for 영역 시작
    System.out.print(1씩 증가되는 숫자);
    System.out.print(".");
    System.out.print("나의 hp : ");
    System.out.println(hp);

    if( hp == 0 ) {
        System.out.println("죽었다");
    }        
    else {
        System.out.println("살아있다");            
    }
    // for 영역 끝    
}
```

여기서 `조건식`과 `1씩 증가되는 숫자` 에는 그럼 무엇을 넣어야할까?

이제부터 진짜 싸움이다.

# 카운팅

일단 코드 복사 붙여넣기를 반복하지 않고 저 `1씩 증가되는 숫자` 자리에 있는 값을 

1,2,3,4,5... 이렇게 늘리고 싶으면 어떻게 해야할까?

계속 숫자가 변한다... 변한다... 

변..

변..ㅅ..

그래!

`변수`를 이용해야 될 것 같다!

`반복문` 위에 새로운 변수 count를 선언 해보자.

``` java
int count;
count = 1;

for( ; 조건식 ; ) {
    // for 영역 시작
    System.out.print(1씩 증가되는 숫자);
    System.out.print(".");
    System.out.print("나의 hp : ");
    System.out.println(hp);

    if( hp == 0 ) {
        System.out.println("죽었다");
    }        
    else {
        System.out.println("살아있다");            
    }
    // for 영역 끝    
}
```

이제 우리는 이 count 변수가 4보다 작을`동안(for)` 반복을 지속 해 볼 것이다.

> count 변수가 4보다 작다 

는 이제 우리가 코드로 표현 할 수 있다.

``` java
count < 4
```

이 코드를 `조건식` 에 옮겨보면

``` java
int count;
count = 1;

for( ; count < 4 ; ) {
    // for 영역 시작
    System.out.print(1씩 증가되는 숫자);
    System.out.print(".");
    System.out.print("나의 hp : ");
    System.out.println(hp);

    if( hp == 0 ) {
        System.out.println("죽었다");
    }        
    else {
        System.out.println("살아있다");            
    }
    // for 영역 끝    
}
```

이렇게 된다.

코드를 해석하면 아래와 같다.

> count 가 4보다 작을 동안 'for 영역 시작' 부터 'for 영역 끝' 까지의 코드를 반복하라

그리고 `1씩 증가되는 숫자` 자리에 count 변수를 출력하도록 변경한 최종 코드는 아래와 같다.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        
        int count;
        count = 1;
        
        for( ; count < 4 ; ) {
            // for 영역 시작
            System.out.print(count);
            System.out.print(".");
            System.out.print("나의 hp : ");
            System.out.println(hp);
        
            if( hp == 0 ) {
                System.out.println("죽었다");
            }        
            else {
                System.out.println("살아있다");            
            }
            // for 영역 끝    
        }
        
        // main의 영역 끝
     }
}
```

"이번 강좌는 왜 이렇게 실행을 안하지?"

라고 슬슬 생각할 때가 왔다.

이제 실행해보자! 

# 무언가 이상하다

우리가 원하는 결과가 잘 출력되었는가? 

분명 그럴리가 없다.

출력되었다면 그것은 오늘 거하게 한잔 하고 몽롱한 상태에서 헛것을 본 것이다.

이쯤에서 `for문`의 코드 실행 순서를 확인해보자.

``` java
for( 1. 초기화 ; 2. 조건식 ; 3. 증감식 ) {
    4. 반복할 코드
}
5. for문 밖 영역
```

for 문은 아래와 같은 순서로 실행된다.

초기화(1)를 실행한다
조건식(2)이 참인지를 확인한다.
참인 경우 영역 안에 있는 코드를 반복(4) 한다.
증감식(3)을 실행한다.
조건식(2)이 참인지를 확인한다.
참인 경우 영역 안에 있는 코드를 반복(4) 한다.
증감식(3)을 실행한다.
조건식(2)이 참인지를 확인한다.
참인 경우 영역 안에 있는 코드를 반복(4) 한다.
증감식(3)을 실행한다.
조건식(2)이 참인지를 확인한다.
참인 경우 영역 안에 있는 코드를 반복(4) 한다.
증감식(3)을 실행한다.
조건식(2)이 참인지를 확인한다.
참인 경우 영역 안에 있는 코드를 반복(4) 한다.
.
.
.
증감식(3)을 실행한다.
조건식(2)이 참인지를 확인한다.
거짓인 경우 for문 영역 밖으로 빠져나온다(5)


숫자로 나열하면

1 24 324 324 324 324 ... 32 5

이 순서로 반복되는 것이다.

``` java
int count;
count = 1;

for( ; count < 4 ; ) {
    // for 영역 시작
    A 코드
    // for 영역 끝    
}
```

여기서 보면 

(초기화 없음)
count < 4 가 참인지 확인
count < 4가 참이므로 A코드 실행
(증감식 없음)
count < 4 가 참인지 확인
count < 4가 참이므로 A코드 실행
(증감식 없음)
count < 4 가 참인지 확인
count < 4가 참이므로 A코드 실행
(증감식 없음)
count < 4 가 참인지 확인
count < 4가 참이므로 A코드 실행
(증감식 없음)
.
.
.
count < 4 가 참인지 확인
count < 4가 참이므로 A코드 실행
(증감식 없음)
count < 4 가 참인지 확인
count < 4가 참이므로 A코드 실행
(증감식 없음)
.
.
.

이 끊임없이 반복 될 뿐이다.

이제는 이 반복을 끝낼 `다른 조건`을 만들어야 한다.

# 증감식 등장이오

현재 count에는 1이 대입되어 있으므로 count < 4 조건은 참(true)이 된다.

저 반복문을 멈추려면 이제 count < 4 가 거짓(false)이어야 한다.

조건이 거짓이려면 count 는 얼마여야하는가?

4 < 4 는 거짓이 되므로 count는 4 이상이어야 한다.

아! 그럼 count를 4로 만들면 되는거야?

빨리 해봐야지

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        
        int count;
        count = 4;  // 여길 바꾸면 되는거구나?
        
        for( ; count < 4 ; ) {
            // for 영역 시작
            System.out.print(count);
            System.out.print(".");
            System.out.print("나의 hp : ");
            System.out.println(hp);
        
            if( hp == 0 ) {
                System.out.println("죽었다");
            }        
            else {
                System.out.println("살아있다");            
            }
            // for 영역 끝    
        }
        
        // main의 영역 끝
     }
}
```

라고 생각해서 저렇게 바꾼 사람이 있을지도 모르겠다.

저상태로 실행을 해보자.

어떤 결과가 나왔는가.

아마 새하얀 도화지가 나왔을 것이다.

이유는 간단하다.

for문의 조건식을 처음 검사할 때부터 `거짓`이기 때문에 

코드를 실행시키지 않고 끝내는 것이다.

그러면 이걸 어떻게 해야 원하는만큼 반복을 시키고 끝낼까..

이럴 때 바로 필요한 것이

>증감식

이다.

count 변수 1을 2로 또 2에서 3으로 만들려면 우리가 알고 있는 선에서는 다음과 같이 해야한다.

``` java
int count;
count = 1;

count = 2;

count = 3;
```

또는 이렇게도 할 수 있다.

```
int count;
count = 1;

count = count + 1;

count = count + 1;
```

> count = count + 1

또 처음보는 방식이다. 위 코드는 

> count + 1 의 결과를 count 에 `대입` 하라

라는 뜻이 된다.

그래서 위 코드를 반복할 때마다 count는 1씩 증가하게 되는 것이다.

그리고 이것을 더 간단한게 쓰면 아래와 같이도 할 수 있다.

```
int count;
count = 1;

count++;

count++;
```

이것을 이제 `증감식` 자리에서 응용해보자.

# 증감식 사용

아까봤던 코드의 증감식 자리에 다음과 같이 넣을 것이다.

``` java
int count;
count = 1;

for( ; count < 4 ; count++ ) {
    // for 영역 시작
    A 코드
    // for 영역 끝    
}
```

실행 순서를 다시 따라가보자.


(초기화 없음)
count < 4 가 참인지 확인
count < 4가 참이므로 `A코드 실행`
`증감식 count++ 실행` ( count가 2가 됨 )
count < 4 가 참인지 확인
count < 4가 참이므로 `A코드 실행`
`증감식 count++ 실행` ( count가 3이 됨 )
count < 4 가 참인지 확인
count < 4가 참이므로 `A코드 실행`
`증감식 count++ 실행` ( count가 4가 됨 )
count < 4 가 참인지 확인
count < 4가 `거짓`이므로 반복문을 나옴

.
.

드디어 `A코드 실행` 이 정확히 3번 실행되고 끝나는 구문이 되었다!

다시 전체코드를 보자


``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20;
        
        int count;
        count = 1;
        
        for( ; count < 4 ; count++ ) {
            // for 영역 시작
            System.out.print(count);
            System.out.print(".");
            System.out.print("나의 hp : ");
            System.out.println(hp);
        
            if( hp == 0 ) {
                System.out.println("죽었다");
            }        
            else {
                System.out.println("살아있다");            
            }
            // for 영역 끝    
        }
        
        // main의 영역 끝
     }
}
```

이걸 다시 실행해보면 이제 다음과 같이 출력 될 것이다.

```
1.나의 hp : 20
살아있다
2.나의 hp : 20
살아있다
3.나의 hp : 20
살아있다
```

드디어! 원하는 결과를 얻어냈다!!

먼 길을 돌아왔지만 이것이 반복문의 모든 것이라고 할 수 있고

이것만 확실히 기억하고 익숙해지면 코드를 잘못 짜서 원하지 않는 동작을 할 때

다시 생각하면서 수정할 수 있는 힘이 생긴다.

# ?? 이게 끝이면 초기화는 뭐죠? 왜 있죠?

무언가 찜찜하다.

반복문을 다 배운거 같은데...

위에서 언급한 한가지를 전혀 사용하지 않았다.

바로 `초기화`!

``` java
int count;
count = 1;

for( 초기화 ; count < 4 ; count++ ) {
    // for 영역 시작
    A 코드
    // for 영역 끝    
}
```

위 코드에서 
``` java
int count;
count = 1;
```

이것이 <u> 변수의 선언, 대입 </u> 과정이라는 것을 알고 있다.

그런데 2장에서 변수를 배울 때 사실 배우지 않은 한가지가 있다.

바로 `선언과 대입을 동시에` 하는 법이다.

``` java
int count = 1;
```

이런식으로 쓰면 `count` 변수를 `선언`하고 바로 1을 `대입` 하게 된다.

그럼 위의 코드를 다시 고쳐 쓰면

``` java
int count = 1;

for( 초기화 ; count < 4 ; count++ ) {
    // for 영역 시작
    A 코드
    // for 영역 끝    
}
```

이렇게 바꿀 수 있고 저 바꾼 코드를 고스란히 초기화 자리에 가져올 수 있다.

``` java

for( int count = 1 ; count < 4 ; count++ ) {
    // for 영역 시작
    A 코드
    // for 영역 끝    
}
```

이제 여느 강좌 책에서 보던 for문의 완벽한 모습이 되었다.

진짜 최종코드의 모습은 아래와 같다.


``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp = 20; // 내친김에 이것도 바꿨다.
        
        for( int count = 1 ; count < 4 ; count++ ) {
            // for 영역 시작
            System.out.print(count);
            System.out.print(".");
            System.out.print("나의 hp : ");
            System.out.println(hp);
        
            if( hp == 0 ) {
                System.out.println("죽었다");
            }        
            else {
                System.out.println("살아있다");            
            }
            // for 영역 끝    
        }
        
        // main의 영역 끝
     }
}
```

# 마치며

반복문은 사실 이게 진짜로 다 배운 것이다. 

모든건 이 기본틀에서의 응용일 뿐이다.

보통 책의 예제 같은 곳에서는 

"0부터 9까지 숫자를 순서대로 출력해보시오" 부터 시작한다.

아래와 같은 코드와 함께

``` java
for( int i = 0 ; i < 10 ; i++ ) {
    System.out.println(i);
}
```

이제 이 코드가 이해가 되는가?

아니면 아직도 머릿속이 아픈 외계어처럼 보이는가?

외계어처럼 보인다면 이 강좌 맨 처음부터 아주 천천히 코드 실행 순서를 따라 해 보면서

머릿속에 로직을 그려보길 권장한다.

# 혼자 해보기

- 1부터 20까지 숫자를 차례대로 출력해보기
- 1부터 20까지 숫자 중 짝수만 출력해보기 ( 연산자 / , % 등을 이용 )
- 강좌 예제 코드에서 반복할 때마다 hp를 10씩 줄여보기

# 다음이야기

내가 원하는 값을 입력 받아서 출력해보자!

그리고 조금 더 변수, 조건문, 반복문 사용에 익숙해지자.

> [사이트 후원하기](https://toon.at/donate/636800116400915381)