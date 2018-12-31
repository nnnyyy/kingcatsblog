---
title: 비전공 직군을 위한 자바스크립트 강좌 - 2. 변수와 상수
date: 2018-12-29 09:52:47
tags:
- 자바
- Java
- 프로그래밍
- 변수
- 상수
categories:
- 프로그래밍
- Java
---

> 이 강좌는 철저히 비전공 직군에게 최대한 쉽게 프로그래밍을 이해시키기 위해 만들었습니다.
> 전공자들에겐 다소 쉽고 지루할 수 있음을 미리 경고합니다.

***

# 잡담

프로그래밍에 대한 깊은 이해를 하는 것은 사실 많은 기본 지식을 필요로 한다.

일단 bit, Byte, KByte 같은 `단위` 의 개념

기본적인 `수학 지식`, 예를 들면 `함수` 의 원리 같은..

어딘가에서 들어봤을 법한 "컴퓨터는 0과 1밖에 몰라" 에 쓰이는 `이진법`

그리고 또 `영문 타자 실력`! ( 안 중요해 보이지만 매우 중요하다 )

사실 이 모든걸 머릿속에 집어넣고 시작하기엔 

지나온 세월에서 너무 모르고 또는 잊고 살고 있었던 것들이라 낯설고 어렵기 마련이다.

.
.
.

그래도 해야한다.

안하면 프로그래밍을 이해할 수 없다.

천천히 설명을 할테니 포기하지 말고 따라왔으면 좋겠다.

***

# 다시 복습

1편에서 사용했던 사이트를 다시 한번 열어보자.

[여기 클릭](https://www.tutorialspoint.com/compile_java_online.php)

``` java
public class HelloWorld{

     public static void main(String []args){
        System.out.println("Hello World");
     }
}
```

그래도 몇번 봤었다고 이전보단 덜 낯설다.


``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        System.out.println("Hello World");
        // main의 영역 끝
     }
}
```

코드를 작성할 때 전에 이야기했던 것처럼 main 영역 안에 작성할 것이다.

모든 프로그램은 main 영역에 작성된 코드를 기반으로 실행된다는 사실을 알아두자.


우리는 전시간에 프로그램을 실행시키면 

Hello World 가 화면에 `출력(output, 出力)` 된다는 사실을 알고 있다. 

그리고 Hello World를 Hello My World로 바꿔서 실행하면 

바뀐 문자열이 `출력`되는 것도 알고 있다. 

화면에 무언가를 `출력` 시키기 위해서는 

> System.out.println(무언가);

를 써줘야 한다는 것을 일단 `암기` 하도록 하자. 

원리를 알려고 파고들기 시작하면 또 재미가 없어진다. 

# 다른걸 출력해보기

이제 저 무언가에 쌍따옴표가 붙은 `문자열` 이 아닌 그냥 `숫자` 10을 넣어보자.


``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        System.out.println(10);
        // main의 영역 끝
     }
}
```

Execute를 눌러 실행해보면 

화면에 10이 `출력` 되는 것을 볼 수 있다.

저 `무언가` 에 `문자`가 아닌 `숫자`를 써도 된다는 사실을 이제 알았다.

# 변수 (變數, variable) 와 상수 ( 常數, constant )

방금 숫자 10을 출력 해 보았다.

저 10은 프로그램이 시작해서 끝날 때 까지 계속 10이다. 

중간에 우리 맘대로 바꿀 수 없다.

이렇게 바꿀 수 없이 고정된 수를 `상수` 라고 한다.

## 변수의 필요성

rpg 게임을 만든다고 생각해보자.

캐릭터를 생성하고 나면 hp 가 주어질 것이고, 

그 hp는 싸울 때마다 깎여야한다.  

그런데 지금 상황은 hp 가 10 으로 고정인 상태인거다.

저 값이 `가변적` 이어야 hp를 줄여주는 행동을 할 수 있다.

일단 게임 만드는 기분이 조금이라도 생기도록 코드를 변경해보자.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        System.out.println("나의 hp :");
        System.out.println(10);
        // main의 영역 끝
     }
}
```

실행하면

```
나의 hp : 
10
```

( 줄바꿈이 매우 거슬리지만 일단 이대로 놔두자 )

그러면 이제 저 10을 `변수`로 만들어서 `출력` 하는 방법을 알아보자.

## 변수의 '선언' 과 '대입'

맨 위의 잡담에서 했던 말을 기억하는가.

> bit, Byte, KByte 같은 `단위` 의 개념

어차피 피할 수 없는 산이기에 넘어야 한다.

컴퓨터 안에 무언가( 우리는 hp )를 저장하기 위해서는 저장공간이 필요하다.

우리는 이제 컴퓨터에게 그 저장공간을 `할당` 해달라고 `선언`을 할 것이다.

컴퓨터 용량에 대해서나 사양을 얘기할 때 "야 램이 몇 기가더라, 그 게임 몇 메가더라"

라는 이야기를 꽤 많이 듣거나 해봤을 것이다.

기가니 메가니 비트니 하는 것들이 전부 컴퓨터의 저장공간의 `단위` 이다.

> bit - Byte - KiloByte - MegaByte - GigaByte - TeraBye

순서는 이렇게 되어있다. ( Tera 뒤에도 더 있지만 흔하게 볼 일은 없다... 아직은 )

이것에 대한 또 자세한 설명은 하면 금방 재미없어지기 시작하기 때문에 뒤로 미루도록 하고, 

결국 우리는 저 단위 중에 bit와 Byte 단위를 사용해 볼 것이다.

얘기가 길어졌는데, 일단 또 코드를 작성해보자.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 10;
        System.out.println("나의 hp :");
        System.out.println(hp);
        // main의 영역 끝
     }
}
```

뭔가 바뀐 것 같고, 뭘 위한 것인지 대충 느낌은 오지만 아직 확실히는 모르겠다.

실행을 해보자.

```
나의 hp : 
10
```

오잉? 결과는 바뀐게 없다.

코드를 아래와 같이 변경해보자.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int hp;
        hp = 20; // 이곳이 바뀌었다.
        System.out.println("나의 hp :");
        System.out.println(hp);
        // main의 영역 끝
     }
}
```

결과는

```
나의 hp : 
20
```

이제 위 코드를 한줄 한줄 차례대로 설명해보겠다.

``` java
int hp;
```

여기서부터 또 외계어 등장이다.

`int`는 어디서 굴러온 것인가. 그리고 hp는 왜 `int` 옆에 썼는가.

일단 `int` 는 `Integer( 정수 )` 의 약자이다. 그리고 `hp` 는 우리가 정해준 `이름` 이다.

위 한 줄을 다시 해석하면 

> "컴퓨터야 정수(숫자)를 담을 수 있는 공간을 주고 그 공간 이름을 hp로 해주렴"

이 된다.

``` java
hp = 20;
```

이 줄 해석은 

> "컴퓨터야 hp로 이름지은 공간에 20을 넣어주렴 ( `대입` 시켜주렴 )

이다.

그리고 마지막으로

``` java
System.out.println(hp);
```

이 한 줄! 이미 눈치야 다 채고 있을 거지만

이 강좌 초반에 썼던걸 다시 가져와보자

> System.out.println(무언가);

이 `무언가`에는 `문자열`, `상수` 가 들어갈 수 있었듯이 `변수`도 넣을 수 있고 우리는 아래와 같이

``` java
System.out.println(hp);
```

hp 라는 `변수`를 `출력` 한 것이다.

# 정리

``` java
int hp;
```

이것을 프로그래머들이 쓰는 용어로 이야기하면

> int 형( Type ) 변수 hp 를 선언 했다.

라고 한다. 

여기서 `int`는 `변수타입` 이고, `hp` 는 `변수명(이름)` 인 것이다.

참고로 `변수타입`은 <u>선언 할 때만</u> 써준다.

``` java
int mp;
int mp = 20; // X
```

이런식으로 같은 이름으로 <u> 두 번 선언하면 안된다 </u>


`hp` 는 우리가 원하는 다른 이름으로 언제든지 변경 가능하다.

``` java
public class HelloWorld{

     public static void main(String []args){
        // main의 영역 시작
        int mp;
        mp = 20;
        System.out.println("나의 mp :");
        System.out.println(mp);
        // main의 영역 끝
     }
}
```

이런식으로 말이다. 

이것을 다시 출력해보면 

```
나의 mp :
20
```

이 될 것이다.

---

# 마치며

변수 개념을 정확히 알고 있어야 앞으로 개고생하지 않는다.

이것저것 바꿔서 테스트 해보는 습관을 들여라~

# 다음이야기

조건에 따라 다르게 표시할 수 있는 `if문` 에 대해서 배워보겠다.

> [사이트 후원하기](https://toon.at/donate/636800116400915381)