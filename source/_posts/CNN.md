---
title: CNN
date : "2022-04-06"
categories:
- [Study]
---


- CNN이란?
    
 Convolutional Neural Network의 약자로 이미지 학습을 위한 효율적이 알고리즘인 합성곱 신경망을 의미한다.    
    
 컬러 사진을 수치 데이터로 변경하면 데이터의 크기가 커지게 되는데 이는 데이터 처리의 어려움을 야기 한다.  
 이 때 CNN을 이용해 데이터 처리를 하게 되는데 대상에 대한 특징을 인식하여 이미지 데이터를 다양한 방법으로 필터링하여 학습시킨다.
    
- CNN 구조
  주로 입력 부근 계층을 합성곱 계층으로 구성하고 출력 층들은 완전 연결 계층으로 분류한다.
    
    ![](/images/CNN/Untitled.png)
    

- CNN 은닉 계층  
  1. 합성곱 Layer
  - 합성곱 연산
    입력 데이터에 필터를 적용해 일정 간격으로 이동해가면서 입력 데이터에 적용한다.
  - 채널
    컬러 이미지는 RGB로 표현한 각 픽셀을 3차원 데이터로 3개의 채널로 구성한다.
  - 패딩
    출력 이미지 사이즈를 그대로 유지 가능하게 한다.
  - 스트라이드
    입력 데이터와 필터를 합성곱할 때 이동할 간격을 제어한다.  
    
  2. Pooling Layer
  -  Pooling 
    sub_sampling을 사용하여 Feature-Map 크기 줄인다. 그 결과 이동에 강한 성질을 갖는 특징을 추출한다.
  -  Max Pooling
    각 픽셀의 최댓값을 뽑아낸다.
  -  Average Pooling
    각 픽셀의 평균값을 뽑아낸다.
  -  Flatten
    2차원, 3차원의 행렬 구조를 1차원의 Vector로 변환한다.  
  
3. 완전 연결 계층 (Fully Connected)
 이전 계층의 모든 노드가 다음 계층의 모든 노드에 연결된 계층
 
---
참고 :[PDF](http://contents2.kocw.or.kr/KOCW/data/document/2020/edu1/bdu/hongseungwook1118/041.pdf)
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**