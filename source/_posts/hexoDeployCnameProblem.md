---
title: github 사이트 custom domain 사용 시, hexo 로 deploy 하면 초기화 되는 문제 해결 방법
date: 2018-12-31 09:47:59
tags:
- github
- hexo
- deploy
- cname
categories:
- 웹프로그래밍
- 기타
---

github를 이용해서 만든 웹사이트는 보통 주소가 

https://[계정아이디].github.io

이런식인데, kingcats.net 같은 커스텀한 도메인을 설정 해 줄 수도 있다.

그런데 [hexo](https://hexo.io/ko/index.html) 를 이용해서 블로그를 만든다음 github 에 deploy 를 하고나면

그 설정이 초기화 되는 경우가 있는데, 

그것은 hexo 가 deploy 를 할 때 기존 github 에 있던 CNAME 이란 파일을 지워버리기 때문이다.

그걸 방지하기 위해 

```
>hexo generate
```

할 때 생기는 

{% asset_img img1.jpg %}

이 public 폴더에 CNAME 파일을 생성해놓으면

문제가 해결 될 것이다.

참고로 내 CNAME 파일에는 이렇게 적혀 있다.

    kingcats.net