---
title: Python 기초 - 사용자 함수 생성
date : "2022-03-22"
categories:
- [Python]
---

- 사용자 함수 만들기 (피타고라스)

```python
import math

def pt(a,b):
  '''피타고라스 정리 - 긴 변의 길이를 구하는 함수
  
  Args:
    m(two int or float)
    
  Returns:
   긴 변의 길이는 : float
    
  '''
  c = a**2 + b**2
  d = math.sqrt(c)
  return(d)

if __name__ == "__main__":
  a = 3
  b = 4
  print('긴 변의 길이는 : ' , pt(a,b))
```

- 평균 / 중간값 구하기 함수

```python
def mean_and_median(value_list):
  '''
  숫자 리스트의 요소들의 평균과 중간값을 구하는 코드를 작성하라
  
  Args:
    value_list (iterable of int / float): A list of int numbers
    
  Returns:
    tuple(float,float)
  '''
  # 평균
  mean = sum(value_list) / len(value_list)

  # 중간값
  midpoint = int(len(value_list) / 2)
  if len(value_list) % 2 == 0:
    median = (value_list[midpoint - 1] + value_list[midpoint])
  else:
    median = value_list[midpoint]

  return mean,median

if __name__ == "__main__":
  value_list = [1,1,2,2,3,4,5]
  avg,median = mean_and_median(value_list)
  print("avg : ", avg)
  print("median : ", median)
```

> if __name__ == "__main__" 사용하는 이유 
 - import 되었을 때 필요한 함수만 불러와 사용할 수 있게 하고,  직접 호출될 때 그 자체로 수행되도록 하기 위함이다.
> 

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**