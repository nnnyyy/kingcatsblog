---
title: hexo(헥소) 간단 설치 및 사용법
date: 2018-12-31 17:55:04
tags:
- hexo
- 웹 블로그
categories: 
- 웹프로그래밍
- 기타
---


[hexo](https://hexo.io/ko/index.html) 는 마크다운 문법이 사용가능한 블로그 프레임워크이다.

(이 사이트가 hexo로 만들어져 있다.)

hexo를 설치하고 실행하기에 앞서 먼저 설치해야 될 두가지가 있다.

---

## git

소스 관리 툴이다.

[window 용 설치 페이지](https://git-scm.com/download/win)
[mac 용 설치 페이지](https://sourceforge.net/projects/git-osx-installer/)

## node.js

javascript 기반 웹 서버 프레임워크이다.

[Node.js 홈페이지](https://nodejs.org/ko/)

---

두가지를 다 설치했다면 이제는 hexo를 설치하도록 한다.

일단 hexo 명령어를 cmd에서 실행하기 위해서

hexo-cli 패키지를 설치한다.

```
>npm install hexo-cli -g
```

( npm 명령어는 node.js 를 설치하면 실행 할 수 있다. )

그리고 

hexo를 설치할 폴더로 들어가서 아래와 같이 실행해준다.

```
>hexo init [폴더명]
```

여기선 TestBlog 로 하겠다.

```
>hexo init TestBlog
```

그 후에 TestBlog 폴더로 들어가서 인스톨을 한다.

```
>cd TestLog
TestBlog>npm install
```

( `npm install` 명령어는 폴더 내에 있는 `package.json` 파일에 있는 모듈을 전부 인스톨 해준다. )

마지막으로 로컬테스트를 위한 hexo 서버를 실행한다.

```
TestBlog>hexo server
```

서버 포트는 기본 4000번으로 되어있다.

다른 포트를 사용하고 싶으면 

```
TestBlog>hexo server -p 4444
```

이렇게 바꾸면 된다.

그 이후 브라우져에서 [http://localhost:4444](http://localhost:4444) 를 입력해보자

기본 블로그 화면이 떴다면 성공!