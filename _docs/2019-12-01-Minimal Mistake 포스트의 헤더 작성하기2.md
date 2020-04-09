---
title: "지킬블로그, Minimal Mistake 포스트 작성하기 - 2"
date: 2019-12-01
comments: true
excerpt: "Liquid와 YAML front matter로 지킬블로그, Minimal Mistake의 포스트를 작성해보자"
categories: "Jekyll"
author_profile: false
header:
  image: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX.jpg"
  teaser: "assets/images/Jekyll.jpg"
toc: true 
toc_label: "이번 포스트에서는 ..." 
toc_icon: "chess-rook"
toc_sticky: true
food: Pizza
city:
    - SEOUL
    - TOKYO
    - L.A.
money: true
---
<!-- POST ID: zV5KAlGEMt -->
<!--Language Button HTML -->
<span><a class="Jekyll"><i class="fab fa-github"></i> Jekyll</a><a class="JekyllVer">4.0.0</a></span>  <span><a class="YAML"><i class="fab fa-yammer"></i> YAML</a><a class="YAMLVer">1.2</a></span>  <span><a class="Liquid"><i class="fas fa-flask"></i> Liquid</a><a class="LiquidVer">4.0.0</a></span>
<!--Language Button HTML -->
<!-- Main content-->

## 개요
지난 포스트, [지킬블로그, Minimal Mistake 포스트 작성하기 - 1]() 에서는 YAML front matter를 사용하여 포스트의 작성하기 전의 다양한 부가기능에 대해서 설명했습니다. 이번 포스트에서는 조금 더 나아가, Liquid 문법과 YAML front matter를 사용하여 조금 더 편리하게 마크다운 포스트를 작성하는 방법에 대해 설명합니다.

## YAML front matter
### 문자열 정렬
class 추가로 문자열을 정렬할 수 있습니다.

~~~markdown
거북이
{: .text-left}
~~~
거북이
{: .text-left}
는 오래 살기로 유명한 동물입니다.<br>
~~~
해파리
{: .text-center}
~~~
해파리<br>
{: .text-center}
는 수족관에서 보면 참 이쁜데요, <br>
~~~
상어
{: .text-right}
~~~
상어<br>
{: .text-right}
는 실제로 만난다면 정말 위험하겠죠?<br>
~~~
Justify는 마지막 줄을 제외한 모든 줄이 
개행에 관계없이 한 줄을 채우는 것을 말합니다. 
좌측정렬과는 비슷하지만 자세히 보면 조금 다른 방식의 정렬입니다.
{: .text-justify}
~~~
Justify는 마지막 줄을 제외한 모든 줄이 
개행에 관계없이 한 줄을 채우는 것을 말합니다. 
좌측정렬과는 비슷하지만 자세히 보면 조금 다른 방식의 정렬입니다. 
{: .text-justify}

### 이미지 정렬
문자열과 비슷하게 이미지 또한 class를 추가하여 정렬할 수 있습니다.

이미지 정렬은 데스크탑 이외의 디바이스에서는 적용되지 않을 수 있습니다.
{: .notice--danger}
~~~markdown
![image-center](/assets/images/post/Jekyll/zV5KAlGEMt_1.jpg)
{: .align-center}
~~~
이렇게 작성된 마크다운은 다음과 같이 표시됩니다.

![image-center](/assets/images/post/Jekyll/zV5KAlGEMt_1.jpg)
{: .align-center}

~~~markdown
![image-left](/assets/images/post/Jekyll/zV5KAlGEMt_2.jpg)
{: .align-left}
~~~
![image-left](/assets/images/post/Jekyll/zV5KAlGEMt_2.jpg)
{: .align-left}
위의 코드는 어떨까요? 가끔씩 문단의 좌측이나 옆에 이미지를 위치시키고 싶을 때가 있습니다. 보시는대로 위와 같이 `{: .align-left}` class를 추가하시면 이미지를 문단의 좌측에 정렬할 수 있습니다. 이미지의 크기를 고려하여 포스트에 이미지를 멋지게 배치하는 것도 포스트를 작성할 때 고려해야 할 중요한 사항입니다. 
~~~markdown
![image-right](/assets/images/post/Jekyll/zV5KAlGEMt_3.jpg)
{: .align-right}
~~~
![image-right](/assets/images/post/Jekyll/zV5KAlGEMt_3.jpg)
{: .align-right}
세번째는 `{: . align-right}` 입니다. 위처럼 작성된 마크다운은 이미지를 어떻게 정렬할까요? 

우측에 정렬된 이미지는 좌측에 정렬된 이미지보다는 다소 크기가 크군요. 이상으로 이미지를 정렬하는 3가지 방법에 대해서 설명하였습니다.

### 사용자 변수(Custom variable)
YAML front matter로 사용자 변수를 정의할 수 있습니다.
~~~yaml
---
food: Pizza
city:
    - SEOUL
    - TOKYO
    - L.A.
money: true
---
~~~
포스트의 최상단에 정의한 변수는 이후 페이지 어디에서도 이 변수를 참조 할 수 있습니다.
{% raw %}
~~~yaml
저는 {{page.food}}를 좋아합니다.
{% for item in page.city %}
<ul>
<li>I love {{item}}</li>
{% endfor %}
</ul>
{% if page.money %}
I am rich! 
{% endif %}
~~~
{% endraw %}

결과는 다음과 같습니다.

저는 {{page.food}}를 좋아합니다.<br>
<ul>
{% for item in page.city %}
<li>I love {{item}}</li>
{% endfor %}
</ul>
{% if page.money %}

I am rich! 
{% endif %}

### 이미지, 동영상 게시(Figure)
마크다운에서는 `![이미지 이름](이미지 주소)`로 이미지를 게시할 수 있습니다. 하지만 Liquid로도 이미지와 동영상을 게시할 수 있습니다.
{% raw %}
~~~
{% include 
    figure 
    image_path="/assets/images/zV5KAlGEMt_3.jpg" 
    alt="Figure image" 
    caption="여기는 이미지 설명, caption입니다." 
    %}
~~~
{% endraw %}
Figure라고 불리우는 이 기능은 하나의 이미지와 캡션을 제공합니다. 속성은 다음과 같습니다. 

|     속성     |      설명       | Remark |
| :--------: | :-----------: | :----: |
| image_path |    이미지의 경로    |   필수   |
|    alt     | 이미지 사용 불가시 대체 |        |
|  capation  |    이미지 설명     |        |

{% include 
    figure 
    image_path="/assets/images/post/Jekyll/zV5KAlGEMt_4.jpg" 
    alt="Figure image" 
    caption="여기는 이미지 설명, caption입니다." 
    %}

또한, 다음과 같이 Liquid 문법으로 마크다운 문서에 동영상을 게시할 수 도 있습니다.

{% raw %}
~~~yaml
{% include video id="JRgQgr4-at8" provider="youtube" %}
~~~
{% endraw %}

{% include video id="JRgQgr4-at8" provider="youtube" %}

유튜브 이외에도 비메오, 구글 드라이브 등 다양한 provider 옵션을 제공합니다.

특정 유튜브 동영상의 경우 게시가 불가능할 수 있습니다. 그럴땐 [이 방법](https://terada-dante.github.io/markdown/markdown03/#embedresponsively)을 사용하셔야합니다.
{: .notice--success}

<!-- Main content-->

<!-- Javascript -->

<!-- Javascript -->

<!-- CSS -->
<style>
img{
    border-radius: 5px;
}
.align-left{
    margin: 5px;
}
.align-right{
    margin: -5px;
}
</style>

<!-- CSS -->
