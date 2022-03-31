---
title: Python - Matplotlib / Seaborn
date : "2022-03-24"
categories:
- [Python]
---
# Matplotlib


```python
import matplotlib.pyplot as plt
```

- 주식 데이터 다운
- !pip install yfinance --upgrade --no-cache-dir


```python
import yfinance as yf
data = yf.download("AAPL", start = "2019-08-01", end = "2022-03-23" )
ts = data['Open']
print(ts.head())
```

    [*********************100%***********************]  1 of 1 completed
    Date
    2019-08-01    53.474998
    2019-08-02    51.382500
    2019-08-05    49.497501
    2019-08-06    49.077499
    2019-08-07    48.852501
    Name: Open, dtype: float64
    


```python
plt.plot(ts)

# pyplot API
plt.title("Stock Market of AAPL")
plt.xlabel("Date")
plt.ylabel("Open Price")
plt.show()
```


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_4_0.png)
    



```python
# fig는 틀만 관리.
fig, ax = plt.subplots()
ax.plot(ts)

# ax.title("Stock Market of AAPL")     ->  Text' object is not callable
# ax.xlabel("Date")
# ax.ylabel("Open Price")

# 객체지향 API
ax.set_title("Stock Market of AAPL")
ax.set_xlabel("Date")
ax.set_ylabel("Open Price")

plt.show()
```


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_5_0.png)
    


## 막대 그래프


```python
import matplotlib.pyplot as plt
import numpy as np
import calendar

month_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
sold_list = [300, 400, 550, 900, 600, 960, 900, 910, 800, 700, 550, 450]
```


```python
fig, ax = plt.subplots(figsize = (10,6))

# 막대 그리기
barplots = ax.bar(month_list, sold_list)

print("barplots : ", barplots)
# <BarContainer object of 12 artists>   ====  맷플랏립의 아키텍트 중 아티스트 층이 12개가 있다.
# 달 하나하나가 artist layer에 존재

# 텍스트 올리기
for plot in barplots:
  # print(plot)
  # print(plot.get_height())
  height = plot.get_height()
  ax.text(plot.get_x() + plot.get_width()/2 , height,height, ha = "center",va = 'bottom' )


plt.xticks(month_list, calendar.month_name[1:13], rotation = 270)
plt.show()
```

    barplots :  <BarContainer object of 12 artists>
    


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_8_1.png)
    


## 산점도


```python
import seaborn as sns

tips = sns.load_dataset("tips")
# print(tips.info())

x = tips['total_bill']
y = tips['tip']

# 산점도
fig, ax = plt.subplots(figsize = (10,6))
ax.scatter(x,y)
ax.set_xlabel('total bill')
ax.set_ylabel('tip')
plt.show()

```


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_10_0.png)
    



```python
# 성별로 data를 묶는다.
label, data = tips.groupby('sex')
# print(label)
# print(data)

# 색상 넣어주기
tips['sex_color'] = tips['sex'].map({'Male' : '#36D6F7', 'Female' : '#F5DC73'})
# print(tips.head())

fig, ax = plt.subplots(figsize=(10,6))
for label, data in tips.groupby('sex'):
  ax.scatter(data['total_bill'],data['tip'], label = label, color = data['sex_color'], alpha = 0.9)
  ax.set_xlabel('total bill')
  ax.set_ylabel('tip')

ax.legend()
plt.show()


```


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_11_0.png)
    


# SeaBorn

- scatter - seaborn


```python
import seaborn as sns
tips = sns.load_dataset("tips")

# plt도 seaborn 적용 가능 - 사이즈 바꿔보기
fig, ax = plt.subplots (figsize = (10,6))
sns.scatterplot(x = 'total_bill', y = 'tip',hue = 'sex', data = tips)
plt.show()
```


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_14_0.png)
    



```python
# plt 적용 전
sns.scatterplot(x = 'total_bill', y = 'tip', data = tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7fd71a8af310>




    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_15_1.png)
    



```python
# 두 개의 그래프를 동시에 반환
fig, ax = plt.subplots(nrows = 1, ncols = 2, figsize = (15,5))
# fit_reg 회귀선?
sns.regplot( x = 'total_bill', y = 'tip', data = tips , ax = ax[0], fit_reg=True)
sns.regplot( x = 'total_bill', y = 'tip', data = tips , ax = ax[1], fit_reg=False)
ax[1].set_title("without linear regression line")
ax[0].set_title("with linear regression line")

```




    Text(0.5, 1.0, 'with linear regression line')




    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_16_1.png)
    


- barplot - seaborn


```python
sns.countplot(x='day',data = tips)
plt.show()
```


    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_18_0.png)
    



```python
print(tips['day'].value_counts().index)
print(tips['day'].value_counts().values)
print(tips['day'].value_counts(ascending=True))
```
결과)
 CategoricalIndex(['Sat', 'Sun', 'Thur', 'Fri'], categories=['Thur', 'Fri', 'Sat', 'Sun'], ordered=False, dtype='category')
 [87 76 62 19]
 Fri     19
 Thur    62
 Sun     76
 Sat     87
 Name: day, dtype: int64
    


```python
fig, ax = plt.subplots()
ax = sns.countplot(x = 'day', data = tips, order = tips['day'].value_counts().index)

# .patches seaborn도 matplot사용하기 위해
for plot in ax.patches:
    height = plot.get_height()
    ax.text(plot.get_x() + plot.get_width()/2 , height,height, ha = "center",va = 'bottom' )

ax.set_ylim(-5,100)

```




    (-5.0, 100.0)




    
![](/images/Matplotlib_Seaborn/Matplotlib_Seaborn_20_1.png)
    
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**