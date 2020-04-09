---
title: "자바스크립트의 잘 알려지지 않은 기능들"
date: 2019-12-14
categories: "Javascript"
excerpt: "자바스크립트에서 많은 사람들이 모르고 있는 꿀팁을 소개합니다."
comments: true
author_profile: false
header:
    image: "/assets/images/head/Javascript_head.jpg"
    teaser: "/assets/images/teaser/Javascript_teaser.jpg"
toc: true 
toc_label: "이번 포스트에서는 ..." 
toc_icon: "chess-rook"
toc_sticky: true
---
<span><a class="Javascript"><i class="fab fa-js-square"></i> Javascript</a><a class="Javascriptver">ES8</a></span>
<!-- Main content-->
## 개요
이번 포스트에서는 사람들에게 잘 알려지지 않은 자바스크립트의 기능들에 대해서 소개하려고 합니다. 저같은 자바스크립트 초보들에게는 상당히 유익한 정보라고 생각됩니다. 여러분들은 이 중에서 얼마나 알고 계신지 한 번 확인해보는게 어떨까요? 

## 터너리 매직(Ternary magic)
터너리 매직의 문법은 다음과 같습니다.
~~~javascript
조건문 ? 참 결과 : 거짓 결과
~~~
직역하면 삼항 마술(?)쯤이 되겠네요. 자바스크립트에서 if문을 작성할 때 유용하게 사용할 수 있는 트릭입니다. 워낙 유명해서 다들 알고 계실 것이라고 생각합니다.<br> 
> 시나리오 : 변수 n이 양수인 경우 'Positive'를 출력하고 음수인 경우 'Negative'를 출력하라.

일반적인 if문을 사용한다면 다음과 같이 작성할 수 있습니다.
~~~javascript
const n = 5
if (n > 0) {
    console.log('Positive')
else {
    console.log('Negative')
    }
// 'Positive' 
~~~
위처럼 작성해도 틀린 것은 아닙니다만 이러한 간단한 if문을 작성할 때에는 다음과 같이 터너리 매직을 사용할 수도 있습니다.
~~~javascript
const n = 5
n > 0 ? console.log('Positive') : console.log('Negative')
// 'Positive'
~~~
위 문법이 더 직관적이고 간단하지 않나요? 
따라서 다음과 같은 상황에서도 유연하게 응용할 수 있습니다.
> 시나리오 : 변수 n이 양수인 경우 'Positive'를 출력하고 음수인 경우 'Negative'를 출력하라. 단, n이 0일 경우 'Zero'를 출력하라.

자바스크립트에도 switch문이 존재하기 때문에 switch를 사용해도 되겠지만 터너리 매직으로 간단히 if문을 대체할 수 있습니다.
~~~javascript
let n = 0
n > 0 ? console.log('Positive')
    : n < 0 ? console.log('Negative') : console.log('Zero')
~~~
위처럼 거짓 결과 부분에 터너리 매직, 새로운 조건문을 작성하면 3가지 조건의 경우에도 if문을 쉽게 작성할 수 있습니다.

## 자동 형 변환
가끔 자바스크립트로 프로그래밍을 하다보면 문자열(string)과 숫자(number)자료형때문에 곤란할 때가 있습니다. 변수의 숫자 1이 문자열 '1'인 경우나, 문자열 '123'이 숫자 123인 경우입니다. 이럴때 간단히 강제 형 변환을 하는 방법이 있습니다.
> 숫자의 경우 `+ ''`, 문자의 경우 `* 1`

숫자에 빈 문자열을 더하면 강제로 숫자➡문자로 형변환이 이루어 집니다.<br> 반대로 문자의 경우 1을 곱해주면 자동적으로 문자➡숫자로 자료형의 변환이 이루어지죠.
~~~javascript
const n = 1
console.log(typeof n)
// number
console.log(typeof (n + ''))
// string

const s = '0'
console.log(typeof s)
// string
console.log(typeof (s * 1))
// number
~~~

## 배열 채우기
자바스크립트에서 배열을 정의하고 배열을 채워야 할 때가 생깁니다. 예를 들어 길이가 5인 배열을 정의하려고 한다면 다음과 같이 작성할 수 있습니다.
~~~javascript
const array = Array(5)
console.log(array)
// [empty x 5]
~~~
그런데 문제는 위처럼 선언한 배열은 **비어있다**라는 것입니다.<br> 하지만 `fill()` 메소드를 사용하면 배열을 선언함과 동시에 정의할 수 있습니다. 

~~~javascript
const array = Array(5).fill('0')
console.log(array)
// [0, 0, 0, 0, 0]
~~~

빈 배열을 선언하는 것과 **null**을 채운 배열을 선언하는 것은 다릅니다!
{: .notice--info}

## 배열 중복 제거
다음과 같은 코드로 배열의 중복을 제거할 수 있습니다.
~~~javascript
Array.from(new Set(배열))
~~~
Set, filter, reduce 등 자바스크립트에서 배열 내 중복을 제거하는 방법은 다양히 존재합니다. 전 이중에서도 이 방법이 가장 간편하다고 생각합니다.
~~~javascript
const array = [
    '사과',
    '오렌지',
    '바나나',
    '키위',
    '오렌지']

console.log(Array.from(new Set(array)))
// ['사과', '오렌지', '바나나', '키위']
~~~

## 동적 배열 할당
`[ ]`를 사용하면 자바스크립트에서 객체(오브젝트)의 키(key)값을 변수로 할당할 수 있습니다. 이 기능은 다이나믹 오브젝트(Dynamic object)라고도 불리웁니다.
~~~javascript
const dynamic = 'Age'
const object = {
  Name: 'ownit',
  [dynamic] : "20"
}

console.log(object)
// { Name: "ownit", Age: "20" }
~~~

## 배열 자르기 
자바스크립트에는 배열의 길이를 확인하는 length 메소드가 있습니다. 이 length를 활용하여 간단하게 필요한만큼의 배열을 잘라낼 수 있습니다. 
~~~javascript
const array = [1, 2, 3, 4, 5, 6]
array.length = 3
console.log(array)
// [1, 2, 3]
~~~
이 방법은 array의 내용을 수정합니다!
{: .notice--danger}
물론 이 방법은 제일 앞을 기준으로 원소를 획득합니다. 따라서 일반적인 경우에서는 slice를 추천합니다.
~~~javascript
const array = [1, 2, 3, 4, 5, 6]
console.log(array.slice(-2))
// [5, 6]
console.log(array.slice(3,-1))
// [4, 5]
console.log(array)
// [1, 2, 3, 4, 5, 6]
~~~

## 배열을 객체(오브젝트)로 변환
다음과 같은 코드로 배열을 객체(오브젝트)로 변환할 수 있습니다.
~~~javascript
const 객체명 = {...배열명}
~~~
{...배열명}이라는 부분이 조금 신선하네요.
~~~javascript
const array = ['A', 'B', 'C']

const object = {...array}
console.log(object)
// {0: 'A', 1: 'B', 2: 'C'}
~~~
반대로 객체를 배열로 변환하는 경우에는 Object.key(객체명)과 Object.value(객체명)를 적절히 사용하면 될 것 같습니다.<br>

혹시 간단한 기능이 있다면 소개해주시길 바랍니다.
{: .notice--success}

## 실행 속도 측정
자바스크립트에서 코드의 성능 측정이나, 실행 속도를 측정할 때 Date() 메소드를 많이 사용합니다. 하지만 자바스크립트는 속도 측정을 위한 메소드, performance를 제공하고 있다는 사실을 알고 계셨나요?

~~~javascript
const start = performance.now()

for(let i =0; i<10000; i++){
  console.log('자바스크립트 코드 속도 측정 중!')
}

const end = performance.now()

console.log(end - start)
// 18564.23322
~~~
위처럼 끝과 시작의 값의 차가 밀리세컨드로 주어지고 이를 코드 실행 속도의 지표로 참고하실 수 있습니다.

## 두 변수 교환
두 개의 변수를 바꿀 때 temp라는 변수를 만들지 않아도 됩니다. 

~~~javascript
let a = 'First'
let b = 'Second'

[a, b] = [b, a]

console.log(a, b)
// 'Second', 'First'
~~~

<!-- Main content-->
