---
title: Plotly - Pie Charts
date : "2022-04-09"
categories:
- [Python]
---


✏️ <span style="color:#871C1C;"> 추가적으로 계속 업데이트  </span>

📎 참고 페이지 : [Plotly 공식 페이지](https://plotly.com/python/pie-charts/)  

  

### Basic Pie Charts

- express version

```python
import plotly.express as px

df = px.data.tips()

# 요일별 팁 현황
fig = px.pie( df , values = 'tip', names = 'day')
# fig.show()
```

![](/images/Plotly_Pie/Untitled.png)

```python
# 성별 팁 현황
fig = px.pie( df , values = 'tip', names = 'sex')
fig.show()
```

![](/images/Plotly_Pie/Untitled%201.png)

values - 시각화할 값  

names - 시각화할 값을 그룹으로 묶는다.  

  

- graph_objects version

```python
import plotly.graph_objects as go

lab = ['Oxygen','Hydrogen','Carbon_Dioxide','Nitrogen']
val = [4500, 2500, 1053, 500]

fig = go.Figure()
fig.add_trace(go.Pie(labels = lab , values = val))
fig.show()
```

![](/images/Plotly_Pie/Untitled%202.png)
  
  
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**