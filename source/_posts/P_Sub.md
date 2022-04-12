---
title: Plotly - Subplot
date : "2022-04-12"
categories:
- [Python]
---


✏️ <span style="color:#871C1C;"> 추가적으로 계속 업데이트  </span>

## **subplots**

Plotly에서 그래프를 행과 열의 형태로 시각화 하기 위해서는 다음 메서드를 따로 불러와야 한다.  

```python
from plotly.subplots import make_subplots
```

기본 틀은 다음과 같이 행과 열의 수를 지정해주면 된다.  

```python
fig = make_subplots(rows = , cols = )
```

  

주의할 점은 그래프 형태 중에서 Pie Chart는 다음과 같이 추가적인 설정이 꼭 필요하다.

```python
fig = make_subplots(rows=1, cols=2, specs=[[{'type':'domain'}, {'type':'domain'}]])
```

`specs`는 만들 형태와 동일하게 만들어 줘야 한다.  

1행 2열인 경우 위와 같이 `specs=[[ {} , {} ]]` 형태로 설정해주고, 2행 1열인 경우에는 다음과 같이 `specs = [[ {} ] , [ {} ]]`설정해주어야 한다.  

그리고 Pie 차트인 경우에는 `{}` 안에 `'type':'domain’` 를 추가로 넣어줘야 한다.
  
  
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**