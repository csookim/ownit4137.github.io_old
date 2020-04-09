---
title: "지킬블로그, Minimal Mistake 포스트 작성하기 - 1"
date: 2019-11-30
comments: true
excerpt: "YAML front matter로 지킬블로그, Minimal Mistake의 포스트를 작성해보자"
categories: "Jekyll"
author_profile: false
header:
  image: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX.jpg"
  teaser: "assets/images/Jekyll.jpg"
toc: true 
toc_label: "이번 포스트에서는 ..." 
toc_icon: "chess-rook"
toc_sticky: true
gallery: 
  - url: "/assets/images/post/Jekyll/3GuM2Rz2dX_1.jpg"
    image_path: /assets/images/post/Jekyll/3GuM2Rz2dX_1.jpg
    alt: "3GuM2Rz2dX_1"
    title: "바다"
  - url: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX_2.jpg"
    image_path: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX_2.jpg"
    alt: "3GuM2Rz2dX_2"
    title: "하늘"
---
<!-- POST ID: 3GuM2Rz2dX -->
<!--Language Button HTML -->
<span><a class="Jekyll"><i class="fab fa-github"></i> Jekyll</a><a class="JekyllVer">4.0.0</a></span>  <span><a class="YAML"><i class="fab fa-yammer"></i> YAML</a><a class="YAMLVer">1.2</a></span>  <span><a class="Liquid"><i class="fas fa-flask"></i> Liquid</a><a class="LiquidVer">4.0.0</a></span>
<!--Language Button HTML -->
<!-- Main content-->

## 개요
블로그 플랫폼의 선택지는 다양합니다. 처음 블로그를 시작할 때는 네이버 블로그나 티스토리 등 편리하고 강력한 블로그가 가장 먼저 눈에 들어왔습니다. 하지만 유명 플랫폼을 선택하지 않고 깃허브의 정적 블로그 지킬(Jekyll)을 선택한 이유는 **확장성**에 있습니다. 내가 원하는 대로 블로그를 제작할 수 있다는 점이 가장 큰 매력이었죠. 하지만 포스팅을 할 때마다 수많은 귀찮은 작업들을 해야하는 것은 그리 생산적인 활동이 아닙니다. 

하지만 고맙게도 Minimal mistake 테마는 단 몇줄의 코드로 목차를 생성해주고, 헤더나 티저 이미지를 생성해주는 등 강력하고 편리한 기능을 제공하고 있습니다. 이번 포스트에서는 Minimal mistake 테마가 포스트를 작성할 때 제공하는 기능, **YAML front matter**에 대해서 설명합니다.

## YAML front matter란?
YAML front matter는 페이지 내용과 페이지의 메타데이터, 구성요소를 설정하고 조정하게 해주는 **선택적인** 기능입니다. 예를 들어 포스트의 excerpt(내용 미리보기)나 카테고리를 설정하는 등의 포스트의 내용을 넘어 **부가적인** 기능을 제공합니다. YAML front matter는 포스트를 작성하기 전 미리 포스트에 필요한 요소들을 설정해두고, 필요에 따라 불러오거나 사용하는 개념입니다.

YAML front matter를 적용하는 법은 간단합니다.
페이지(마크다운 파일)의 최상단에 다음과 같은 코드를 입력합니다.

~~~yaml
---
YAML front matter 코드
---
~~~

YAML front matter 코드를 감싸는 - - -는 생략할 수 없습니다.
{: .notice--danger}

YAML front matter 코드는 기본적으로 `속성: 값`의 형태를 가집니다. 

## YAML front matter
### 기본 요소

포스트를 구성하는 기본요소입니다.

~~~yaml
layout: default
title: "Minimal Mistake 포스트의 헤더 작성하기" 
date: 2019-11-30 12:39:40
comments: true
excerpt: "Minimal Mistake 포스트의 헤더 작성하기, YAML front matter"
~~~

|   속성    |      설명      |      Remark       |
| :-----: | :----------: | :---------------: |
| layout  | 페이지 레이아웃 설정  |  Default: single  |
|  title  |    포스트 제목    |         -         |
|  date   |  포스트 작성 시각   |     시-분-초는 선택     |
| comment | 포스트 댓글 허용 여부 |         -         |
| excerpt | 포스트 내용 미리보기  | Default: 페이지 첫 문단 |


### 포스트 분류

포스트는 2가지 방법, `tag`(태그)와 `category`(카테고리), 으로 분류할 수 있습니다.

~~~yaml
tags:
    - tag1
    - tag2

categories: "category_a category_b"
~~~

|     속성     |  설명   | Remark |
| :--------: | :---: | :----: |
|    tag     |  태그   |   -    |
| categories | 카테고리  |   -    |

태그와 카테고리를 동시에 사용할 수 있습니다. 띄어쓰기와 -, - 개행은 서로 다른 태그 혹은 카테고리를 정의합니다.
{: .notice--info}

### 목차

포스트의 `<h1>, <h2> ...`요소로 목차를 생성할 수 있습니다.

~~~yaml
toc: true 
toc_label: "이번 포스트에서는 ..." 
toc_icon: "chess-rook"
toc_sticky: true
~~~

|     속성     |         설명          |     Remark     |
| :--------: | :-----------------: | :------------: |
|    toc     |      목차 생성 여부       |       -        |
| toc_label  |       목차 타이틀        |       -        |
|  toc_icon  | Font Awesome 아이콘 지정 |     아이콘 이름     |
| toc_sticky |   목차 요소 sticky 여부   | Default: false |

### 포스트 헤더
`image` 속성과 `teaser` 속성은 `header` 속성 내부에서 선언됩니다.
~~~yaml
header:
   image: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX.jpg"
   teaser: "assets/images/Jekyll.jpg"
~~~

|   속성   |   설명   | Remark |
| :----: | :----: | :----: |
| header | 헤더 속성  |   -    |
| image  | 헤더 이미지 |   -    |
| teaser | 티저 이미지 |   -    |


### 이미지 갤러리
이미지 갤러리를 사용하여 문서내부에서 이미지를 나열할 수 있습니다. 
~~~yaml
gallery: 
  - url: "/assets/images/post/Jekyll/3GuM2Rz2dX_1.jpg"
    image_path: "/assets/images/post/Jekyll/3GuM2Rz2dX_1.jpg"
    alt: "3GuM2Rz2dX_1"
    title: "바다"
  - url: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX_2.jpg"
    image_path: "https://raw.githubusercontent.com/TERADA-DANTE/TERADA-DANTE.github.io/master/_images/post/Jekyll/3GuM2Rz2dX_2.jpg"
    alt: "3GuM2Rz2dX_2"
    title: "하늘"
~~~

|     속성     |       설명        |   Remark    |
| :--------: | :-------------: | :---------: |
|  gallery   |   이미지 갤러리 속성    |      -      |
|    url     | 이미지 클릭시 이동할 링크  |      -      |
| image_path |     이미지의 주소     |    필수요소     |
|    alt     | 이미지 사용불가시 대체 설명 |     alt     |
|   title    |     이미지 설명      | placeholder |

YAML front matter에 선언한 이미지 갤러리를 본문에서 다음과 같이 사용할 수 있습니다.
{% raw %}
~~~yaml
{% include gallery caption="마크다운이 적용되는 **캡션**" %}
~~~
{% endraw %}

{% include gallery caption="마크다운이 적용되는 **캡션**" %}

### 기타
~~~yaml
author_profile: false 
read_time: true 
permalink: /Jekyll/
~~~

|       속성       |     설명     |    Remark     |
| :------------: | :--------: | :-----------: |
| author_profile |  프로필 출력여부  | Default: true |
|   read_time    | 열람시간 출력여부  |  1 min read   |
|   permalink    | 웹페이지 경로 설정 |       -       |

<!-- Main content-->

<!-- Javascript -->

<!-- Javascript -->

<!-- CSS -->

<!-- CSS -->
