---
title: webpack 구조에서 .Vue 파일로 Template 을 사용할 때 Adfit(애드핏) 광고 제대로 나오게 하기
date: 2018-12-30 22:49:05
tags: 
- Vue
- 애드핏
- Adfit
- webpack
categories: 
- 웹프로그래밍
- Vue
---

애드핏에서 광고를 만들면 아래와 같은 코드를 광고 삽입 위치에 넣으라고 나온다.

``` javascript
<ins class="kakao_ad_area" style="display:none;" 
 data-ad-unit    = "**********" 
 data-ad-width   = "320" 
 data-ad-height  = "50"></ins> 
<script type="text/javascript" src="//t1.daumcdn.net/adfit/static/ad.min.js" async></script>
```

보통같으면 광고 출력을 원하는 위치에 바로 코드를 삽입하면 되는 일이지만

webpack에서 vue를 모듈화 시켜서 사용 할 때의 .Vue 파일은 아래와 같이 구성되어 있다.

``` html
<template>
</template>

<script>    
    export default {        
        data: function () {
            return {                
            };
        }        
    }
</script>

<style scoped>    
</style>
```

여기에 무턱대고

``` html
<template>
    <div>
        <ins class="kakao_ad_area" style="display:none;" 
        data-ad-unit    = "**********" 
        data-ad-width   = "320" 
        data-ad-height  = "50"></ins> 
        <script type="text/javascript" src="//t1.daumcdn.net/adfit/static/ad.min.js" async></script>        
    </div>
</template>

<script>    
    export default {        
        data: function () {
            return {                
            };
        }        
    }
</script>

<style scoped>    
</style>
```

이렇게 넣으면 vue-parser 에서 오류가 발생한다. 저 template 태그 안에 script 태그를 파싱을 못해서 그런듯하다.

그렇다고 

``` javascript
<script type="text/javascript" src="//t1.daumcdn.net/adfit/static/ad.min.js" async></script>        
```

이 코드만 따로 떼어내서 html의 헤더나 본문에 직접 붙여넣으면 광고가 어떤 때에는 나왔다가 

어떤 때에는 또 안나오는 현상이 발생한다.

이럴 때에는 다음과 같이 조치하면 된다.

``` html
<template>
    <div>
        <ins class="kakao_ad_area" style="display:none;width:100%"
             :data-ad-unit="**********"
             data-ad-width   = "320"
             data-ad-height  = "50"></ins>
        <div v-el:scriptHolder></div>
    </div>
</template>

<script>
    import $ from 'jquery';
    export default {        
        data: function () {
            return {
                
            };
        },        
        mounted: function() {
            const v = this;
            $(document).ready(function() {
                let scriptEl = document.createElement('script');
                scriptEl.setAttribute('src', '//t1.daumcdn.net/adfit/static/ad.min.js');
                scriptEl.async = true;
                document.head.appendChild(scriptEl);
                document.body.appendChild(scriptEl);
            });
        }
    }
</script>

<style scoped>    
</style>
```

jquery를 이용해서 document 가 준비 완료 되고나면 그 이후에 동적으로 

애드핏용 스크립트 코드를 삽입하는 방식이다.

이렇게하면 애드핏 광고가 문제없이 잘 나온다.

> [사이트 후원하기](https://toon.at/donate/636800116400915381)