---
title: mysql 데이터 백업하기
date: 2018-12-31 10:10:14
tags: 
- 노드
- Node.js
- 버전 체크
categories: 
- 웹프로그래밍
- Node.js
---

mysql 데이터 백업은 mysql 을 설치할 때 bin 폴더에 생기는 mysqldump.exe 로 할 수 있다.

```
>mysqldump -u[계정명] -p [데이터베이스명] > [저장할 경로 및 파일명]
```

로 간단하게 할 수 있다.

여기에 Stored Procedure 까지 함께 추출하고 싶다면 

```
>mysqldump -u[계정명] -p --routines [데이터베이스명] > [저장할 경로 및 파일명]
```

`--routines` 를 추가 해주면 된다.

만약 실행 시에 access denied 가 뜬다면 cmd 창을 `관리자 권한`으로 띄워서 다시 해보자.


> [사이트 후원하기](https://toon.at/donate/636800116400915381)