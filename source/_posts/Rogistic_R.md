---
title: Rogistic Regression
date : "2022-03-29"
categories:
- [Study]
---


- Rogistic Regression?
    
지도 학습 알고리즘으로 이진 분류에서는 데이터가 범주에 속할 확률을 0 ~ 1로 두고, 0.5를 기준으로 0과 1 중 어디에 더 가까운 값인지 판단하여 데이터를 분류하는 모델이다.
    
Rogistic Regression의 식과 표를 나타내면 다음과 같다.
    
이 식을 로지스틱 함수 또는 시그모이드 함수 라고도 한다.
    
    
f(x) = 1 / (1+e^-z)
    
    
![](/images/Rogistic_R/Untitled.png)
    
Rogistic Regression 는 이진 분류만 가능한 것이 아니라 다중 분류에서도 사용된다.
    이때는 확률로 변환 시켜 줄 때 시그모이드 함수가 아니라 소프트 맥스 함수를 사용한다.
    
- 왜 Rogistic Regression 이 중요한가?
  Rogistic Regression은 독립 변수와 종속 변수의 설명 관점에서 선형 회귀 분석과 유사한데 Rogistic은 종속 변수가 범주형 데이터로 분류 모델로도 볼 수 있다.

 만약 종속 변수가 음수 값을 갖을 수 없는 데이터인데 선형 회귀에 따라 음수 값이 출력이 되는 경우가 있다. 이를 해결하기 위해 Rogistic Regression을 사용한다.

- Linear Regression vs Rogistic Regression
    
    선형 회귀의 결과 값 : 연속적인 값
    
    로지스틱 회귀의 결과 값 : 범주 값
    
    
 날씨로 예를 들면 선형 회귀의 결과는 온도가 23,24,25와 같은 값을 출력하고 로지스틱 결과는 날씨가 ‘덥다’와 ‘춥다’로 나뉜다.
    
---
- 다음 영상을 참고 : [Youtube](https://youtu.be/zASrGSHoqL4)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**