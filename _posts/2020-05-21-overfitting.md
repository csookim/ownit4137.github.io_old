---
title: "Overfitting"
date: 2020-05-21
categories: "MachineLearning" # 카테고리
excerpt: "학습 과정에서 발생하는 과적합(Overfitting)"
published : true # 공개

author_profile: false
header:
    teaser: "/assets/images/teaser/mllec.jpg"   # 작은 글일때의 이미지

toc: true #Table Of Contents 목차 보여줌
toc_label: " " # toc 이름 정의
toc_icon: " " #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
use_math: true
---

> Machine Learning by Andrew Ng WEEK 3

# Overfitting

## 정의

- 과적합
- 가설 함수의 항이 과하게 많아질수록 그래프에 불필요한 curve가 많아짐

![of](/assets/posts/ml/overfit01.jpg)

그래프 1
  - Underfit, High bias
  - 그래프가 강한 편향을 가지고 있음(데이터의 분포와 거리가 먼 개형)

그래프 2
  - 그래프가 데이터를 적절히 표현

그래프 3
  - **Overfit** , High variance
  - 그래프의 변동성이 큼
  - 새로운 예제가 들어올 경우 일반화된 예측을 하지 못할 수 있음


## 해결 방안

1. Reduce the number of features
  - 불필요한 feature($x_{i}$)을 제외시켜 개수를 줄임
  - Model selection algorithm 사용

2. Regularization
  - 정규화를 통해 $\theta_{i}$의 범위를 줄임
  - feature의 개수를 줄일 필요가 없음
