---
title: "자바스크립트의 조건문, Switch 문에 대하여"
date: 2020-01-22
categories: "Javascript"
excerpt: "자바스크립트의 조건문에는 if else 구문과 switch 구문이 있습니다."
comments: true
author_profile: false
header:
    image: "/assets/images/head/javascriptSwitch_head.jpg"
    teaser: "/assets/images/teaser/Javascript_teaser.jpg"
toc: true 
toc_label: "이번 포스트에서는 ..." 
toc_icon: "chess-rook"
toc_sticky: true
---

<span><a class="Javascript"><i class="fab fa-js-square"></i> Javascript</a><a class="Javascriptver">ES8</a></span>

<!-- Main content-->
## 개요
2020년에 들어서 첫 포스트를 작성하네요. 이것저것 바쁜 일도 많았고, 새로운 프로젝트를 시작하면서 포스팅에 많이 신경을 못썼습니다. 모처럼 시간이 생긴 김에 간단하게 자바스크립트의 Switch 문에 대하여 설명하도록 하겠습니다.

## Switch
Switch문으로 조건문을 작성하는 것은 간단합니다.
~~~javascript
switch (변수) {
    case 값1: 실행할 로직
        break
    case 값2: 실행할 로직
        break
    case 값3: 실행할 로직
        break
    default: 실행할 로직
        break
}
~~~

각 case가 `if(값 == 변수)`를 실행하고 있다고 생각하면 이해에 도움이 됩니다. 

if else 구문과 switch 구문의 대조적인 특징은 **논리의 흐름**에 있습니다.
if else 구문은 순차적으로, 마치 게이트를 통과하듯이, A인가 아닌가, B인가 아닌가, C인가 아닌가를 일일히 검사합니다. 이렇게 조건의 만족 여부를 판단하는 모습이 가지가 뻗어나가는 것과 비슷하다고 하여 branch statement라고 부릅니다.<br>
반면에 switch는 값이 일치하는 case로 이동하여 로직을 수행하기 때문에 jump statement라고 부릅니다. switch 문의 점프 테이블은 바로 어떤 로직을 실행할지 컴파일러가 미리 만들어 놓은 논리 회로인 것이죠.

## if vs switch 성능
개인적인 생각입니다만, 언어마다 그 차이가 있가 있고 컴파일러에 따라 차이가 있겠지만 극단적인 경우를 제외하면 if문이든 switch문이든 비슷한 성능을 보인다고 생각합니다. 
if문을 통과할때마다 논리점검(인스트럭션이라고 합니다)이 필요하므로 직관적으로는 switch문이 더 좋은 성능을 가질 것이라 예상이 되지만 마찬가지로 switch문 또한 점프 테이블을 생성하는 임무(오버헤드라고 합니다.)를 가지고 있습니다. 거시적인 관점에서 보면 물론 둘 다 빠른 연산이지만 이 부분에서는 누군가 정확한 실험을 해주었으면 하는 바람입니다.

성능을 떠나서 생각해보면 확실히 switch 문이 가독성이 좋은 것은 사실입니다. 저의 경우에도 서버와 통신을 하는 리액트 웹 애플리케이션을 제작할 때 HTTP 스테이터스 코드(200, 404, 401 등)에 맞추어 switch 문으로 로직을 제작하였습니다. 

## 마치며
혹자는 3개 이상의 if문에 대하여는 switch문이 그 이하는 if else 구문이 유리하다고 설명합니다. 진실은 어떨지 모르겠습니다. 여러분들의 생각은 어떠신가요?


<!-- Main content-->
