---
title: "Machine Learning Diagnostic"
date: 2020-07-19
categories: "MachineLearning" # 카테고리
excerpt: "Evaluate the learning algorithms"
published : true # 공개

author_profile: false
header:
    teaser: "/assets/images/teaser/mllec.jpg"   # 작은 글일때의 이미지

toc: true #Table Of Contents 목차 보여줌
toc_label: " " # toc 이름 정의
toc_icon: " " #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
use_math: true # mathjax
---


# Evaluating

## Debugging

- 주어진 training set을 바탕으로 예측을 했을 때, 오차가 크게 발생할 경우 여러가지 방법을 취할 수 있음
  - training set을 추가한다
  - feature을 줄이거나 늘린다
  - $\lambda$ 를 줄이거나 늘린다
- 이 방법들을 랜덤하게 시도하기 보다는, 더 체계적인 방법을 시도해야 함

## Splitting

- Dataset들을 Training set(학습용) 과 Test set(테스트)으로 나눔
- Training set에서의 오차를 최소화시키고($J(\theta)$) Test set의 오차($J_{test}(\theta)$)를 계산하여 분석
- Train / Cross Validation / Test Set 세 개로 나누기도 함

# Bias vs. Variance

## degree에 따른 분석

- $J(\theta)$와 $J_{cv}(\theta)$의 관계를 통해 fitting의 문제를 판정

![](/assets/posts/ml/4b48041c.png)

- bias(편향이 크다): Underfitting
- variance(변동성이 크다): Overfitting

## $\lambda$에 따른 분석

- regularization parameter $\lambda$를 다르게 하여 여러 번 test를 수행

![](/assets/posts/ml/227692d0.png)

- Using the best combo $\Theta$ and $\lambda$, apply it on $J_{test}(\Theta)$ to see if it has a good generalization of the problem.

## Data Size에 따른 분석

![](/assets/posts/ml/60f5c9f1.png)

- high bias: 데이터의 크기가 커져도 딱히 차이 없음
- high variance: 데이터의 크기가 커지면 test error가 줄어듬

## Neural Network에서의 분석

![](/assets/posts/ml/c4c69600.png)

- Using a single hidden layer is a good starting default. You can train your neural network on a number of hidden layers using your cross validation set. You can then select the one that performs best.
