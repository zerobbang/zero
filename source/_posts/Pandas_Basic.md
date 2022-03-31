---
title: Python 기초 - Pandas
date : "2022-03-23"
categories:
- [Python]
---


- Pandas 자료 구조 살펴보기
1. Data Frame
    
    ```python
    t_dict = {"col1" : [1,2,3],
              "col2" : [3,4,5]}
    
    df = pd.DataFrame(t_dict)
    print(type(df))
    df
    ```
    
    ![](/images/Pandas_Basic/Untitled.png)
    
2. Series
    
    ```python
    t_dict = {'a':[1,1],'b':2,'c':3}
    ser = pd.Series(t_dict)
    print(type(ser))
    ser
    ```
    
    ![](/images/Pandas_Basic/Untitled%201.png)
    

- Google Drive 통해 데이터 불러오기
    
    ```python
    from google.colab import drive
    drive.mount('/content/drive')
    # 연동 확인 눌러주기
    juice = pd.read_csv("Lemonade2016.csv")
    juice.head()
    ```
    
    직접 현재 경로에 올려서 바로 불러오기도 가능
    

---

### 데이터 구조 확인

```python
juice.info()
```

<aside>
🍒 <class 'pandas.core.frame.DataFrame'>
RangeIndex: 32 entries, 0 to 31
Data columns (total 7 columns):

Column Non-Null Count Dtype

0   Date         31 non-null     object
1   Location     32 non-null     object
2   Lemon        32 non-null     int64
3   Orange       32 non-null     int64
4   Temperature  32 non-null     int64
5   Leaflets     31 non-null     float64
6   Price        32 non-null     float64
dtypes: float64(2), int64(3), object(2)
memory usage: 1.9+ KB

</aside>

→ date와 leaflets에 결측치가 있다.

### Describe ( )

- 기술 통계량 확인 함수 (문자는 취급 X)
    
    ```python
    juice.describe()
    ```
    
    ![](/images/Pandas_Basic/Untitled%202.png)
    
- 문자 확인 → value_counts
    
    ```python
    print(juice['Location'].value_counts())
    print(type(juice['Location'].value_counts()))
    ```
    
    <aside>
    🍒 Beach    17
    Park     15
    Name: Location, dtype: int64
    <class 'pandas.core.series.Series'>
    
    </aside>
    

### 행과 열 다루기

- 컬럼 추가
    
    ```python
    juice['Sold'] = 0
    print(juice.head(3))
    ```
    
    ![](/images/Pandas_Basic/Untitled%203.png)
    
    ```python
    # 새로 생성한 컬럼에 값 추가하기
    juice['Sold'] = juice['Lemon'] + juice['Orange']
    print(juice.head(3))
    ```
    
    ![](/images/Pandas_Basic/Untitled%204.png)
    
- 컬럼 삭제
    
    drop (axis = 0 or 1)
    
    - 0으로 설정시 행(인덱스)방향으로 드롭
    - 1로 설정시 열방향으로 드롭
    
    ```python
    # 열 삭제 axis = 1
    juice_column_drop = juice.drop('Sold',axis = 1)
    print(juice_column_drop.head())
    ```
    
    ![](/images/Pandas_Basic/Untitled%205.png)
    
    - 먄약 축 방향이 잘못될 경우 -> [''] not found in axis. 에러
    
    ```python
    # 행 삭제 axis = 0
    juice_row_drop = juice.drop(0,axis = 0)
    print(juice_row_drop.head(2))
    ```
    
    ![](/images/Pandas_Basic/Untitled%206.png)
    

### Data Indexing

```python
juice[2:9:2]
```

![](/images/Pandas_Basic/Untitled%207.png)

데이터프레임도 인덱싱이 가능하다.

### 조건 주기 (논리값)

```python
juice[juice['Location'] == 'Beach']
```

juice['Location'] == 'Beach'에서 TRUE만 해당되는 값을 가져왔다.

### iloc  / loc

![](/images/Pandas_Basic/Untitled%208.png)

- iloc
    
    ```python
    # [행, 열]
    juice.iloc[0:3,0:2]
    ```
    
    ![](/images/Pandas_Basic/Untitled%209.png)
    
- loc
    
    라벨 기반이기때문에 입력한 값까지 출력이 된다. 
    
    ```python
    juice.loc[:2,:'Location']
    ```
    
    ![](/images/Pandas_Basic/Untitled%209.png)
    
- 조건 / loc
    
    ```python
    # boolen / iloc은 안된다. 
    juice.loc[juice['Leaflets'] >= 100, ['Date','Location']]
    ```
    

### 정렬

```python
# rest_index 정렬한 순으로 인덱스 다시 부여
juice2 = juice.sort_values(by=['Price','Temperature'],ascending = [False,False]).reset_index(drop=True)
juice2.head()
```

Price로 먼저 내림차순 정렬 후, Temperature로 내림차순 정렬한다.
rest_index 정렬한 순으로 인덱스를 다시 부여한다.

### Group By

```python
import numpy as np
juice.groupby(['Location'])[['Revenue','Lemon']].agg([max, min, sum, np.mean])
```

→ Location별로 Revenue와 Lemon의 max,min,sum,mean을 구하여 정리한다.

![](/images/Pandas_Basic/Untitled%2010.png)

---

- 새로운 데이터로 연습

```python
sales = pd.read_csv("supermarket_sales.csv")
```

### Group By 추가

```python
# Product line 별 Quantity의 합계
sales.groupby('Product line')['Quantity'].sum()
sales.groupby(['Customer type','Branch'])['Quantity'].agg(['sum','mean'])
```

→ 이때 데이터 타입은 Series로 변환된다.

? - 다시 Data Frame으로 변환하려면?

```python
sales.groupby(['Customer type','Branch'], as_index = False )['Quantity'].sum()
```

→  as_index = False 해주기

### 결측치

- 문자열 타입이랑 숫자 타입이랑 접근 방법이 다르다.
- 문자 : 빈도 --> 가장 많이 나타나는 문자열 넣어주기, 최빈값
- 숫자 : 평균,최대,최소,중간,임의값 등

```python
dict_1 = {
'Score_A' : [80,90,np.nan,80],
'Score_B' : [30,45,np.nan,np.nan],
'Score_C' : [np.nan, 50,25,40]
}
df = pd.DataFrame(dict_1)
```

![](/images/Pandas_Basic/Untitled%2011.png)

- 결측치 확인하기
    
    ```python
    df.isnull().sum()
    ```
    
    <aside>
    🍒 Score_A    1
    Score_B    2
    Score_C    1
    dtype: int64
    
    </aside>
    
- 결측치에 값 넣어주기
    
    ```python
    # 결측치 자리에 0 넣기
    df.fillna(0)
    
    # 결측치 자리에 그 전 값을 그대로 물려 받기
    df.fillna(method='pad')
    
    # 하나의 결측치만 값을 넣기
    df['Score_C'].fillna(100)
    ```
    
- 결측치 삭제
    - 결측치가 없는 열 넣어주기
        
        ```python
        df['Score_D'] = [10,20,30,40]
        ```
        
        ![](/images/Pandas_Basic/Untitled%2012.png)
        
    - 결측치가 있는 열 삭제 ( axis = 1 )
        
        ```python
        df.dropna(axis = 1)
        ```
        
        ![](/images/Pandas_Basic/Untitled%2013.png)
        
    - 결측치가 있는 행 삭제 ( axis = 0 )
        
        ```python
        df.dropna(axis=0)
        ```
        
        ![](/images/Pandas_Basic/Untitled%2014.png)
        

### 이상치

- 이상치의 하한 경계값 : q1 - (1.5 * (q3 -q1))
- 이상치의 상한 경계값 : q3 + (1.5 * (q3 -q1))

```python
Q1 = sales['Unit price'].quantile(0.25)
Q3 = sales['Unit price'].quantile(0.75)

# Q1 보다 낮은 값을 이상치로 간주
outliers_q1 = (sales['Unit price'] < Q1)

# Q3 보다 낮은 값을 이상치로 간주
outliers_q3 = (sales['Unit price'] > Q3)

# outliers_q1  -> True, False 값으로 나온다.
# 이상치 제거한 값 불러오기
print(sales['Unit price'][~(outliers_q1 | outliers_q3)])
```

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**