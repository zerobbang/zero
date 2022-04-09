
---
title: Decision Tree
date : "2022-03-30"
categories:
- [Study]
---

- Deicision Tree
    
 분류와 회귀가 모두 가능한 지도 학습 모델 중 하나로 조건문을 통해서 가지가 뻗어나가는 형태이다. 다시 말해 데이터의 특성들의 기준으로 데이터를 분류해나가는 모델이다.

이를 토대로 랜덤 포레스트 알고리즘이 탄생했는데 이는 의사 결정 트리 모델 여러개를 훈련시켜 예측하는 앙상블 알고리즘이다. 이처럼 의사 결정 트리를 토대로 MS 또는 Google에서 새로운 알고리즘을 만들고 있어 의사 결정 트리에 대한 기본적인 지식이 꼭 필요하다.

또한 현업에서는 랜덤 포레스트를 비롯한 XGBoost, LightGBM, CatBoost 알고리즘을 사용하기 때문에 의사 결정 트리 또한 꼭 알고 넘어가야 할 알고리즘이다.
    
 ![](/images/DecisionTree/Untitled.png)`

 와인 데이터를 이용해 만든 결정 트리 모델의 일부 모형을 시각화하여 표현 것이다.
    
 네모난 상자를 노드라고 하며 맨 위의 노드를 루트 노드라고 부른다. 그리고 각 노드에 의해 분류된 데이터 값인 value[ a , b]에서 a는 음성 클래스, b는 양성 클래스라고 명칭한다.
    
- 특성 중요도
    
    다음 코드를 입력하여 가지치기를 한 의사 결정 트리를 구할 수 있다.
    
    ```python
    plt.figure(figsize = (20,15))
    plot_tree(dt, filled = True, feature_names = ['alcohol','sugar','pH'])
    plt.show()
    ```
    
    ![](/images/DecisionTree/Untitled%201.png)
    
    자세히 보면 처음에는 당도를 우선으로 분류였고 그 다음은 도수 기준으로 분류할 것을 볼 수 있는데 이는 의사 결정 트리가 자체적으로 특성들 사이에서 중요도를 계산하여 우선적으로 분류 기준으로 할 특성들을 결정한 것이다.
    
    이를 특성 중요도라고 하며 자체적으로 계산한 특성 중요도 값을 살펴보면 다음과 같다.
    
    ```python
    print(dt.feature_importances_)
    ```
    
![](/images/DecisionTree/Untitled%202.png)

→ feature_names 로 지정한 순서대로 나온 결과값으로 당도의 특성 중요도가 가장 높고 그 다음으로 도수가 가장 높다.
    

- gini (불순도)
    
위 결정 트리에서 gini 값이 있는데 이는 불순도를 의미하며 음성 클래스와 양성 클래스의 차이가 크지 않으면 불순도가 높다고 측정 된다. 즉,  한쪽으로 많이 분류되어야 분류가 잘 되었다고 판단하는데, 그래야 해당 노드 안에서 서로 다른 데이터가 많이 섞이지 않았다는 것을 의미하기 때문이다.
    
 우리는 이 불순도를 최소화하는 방향으로 분석해야 한다.
    


---
💻 [실습코드](https://github.com/zerobbang/study_colab/blob/main/hongong/ch5_1_DecisionTree.ipynb)  
📖 [혼자 공부하는 머신러닝 + 딥러닝](http://www.yes24.com/Product/Goods/96024871)  
  
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**