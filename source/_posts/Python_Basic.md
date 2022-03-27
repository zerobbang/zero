---
title: Python 기초 문법 정리
categories:
- [Python]
---
### 형변환 하기

```python
x = input("숫자를 입력하세요 : ")
y = int(input("숫자를 입력하세요 : "))
print(type(x),type(y))
```

→ x : str 문자열, y : int 정수형

이런 방법으로 문자열을 정수형, 실수형, 논리형으로 바꿀 수 있다.

### 인덱싱

- 문자열에서 원하는 자리값의 문자를 가져온다.
    
    ```python
    x = "Hello Kaggle!"
    print(x[6])
    ```
    
    → H부터 자리 0으로 자리 6번째인 K가 출력 된다. (공백도 포함하여 계산)
    

### 슬라이싱

- 문자열에서 범위를 지정하여 값을 가져온다.
    
    ```python
    x = "Hello Kaggle!"
    ```
    
    ```python
    print(x[:])
    ```
    
    → Hello Kaggle!
    
    ```python
    print(x[6:])
    ```
    
    → Kaggle!
    
    ```python
    print(x[6:8])  # 앞 숫자 부터 뒷수자 -1까지 보여준다.
    ```
    
    → Ka
    
    ```python
    print(x[0:9:2]) # 지정한 범위내에서 2씩 간격을 두고 뽑아낸다.
    ```
    
    → Hlo
    

### 포매팅 format

- %s : 문자열
- %c : 문자 1개
- %d : 정수
- %f : 부동소수
- %o : 8진수
- %x : 16진수
- %% : Literal %(문자 % 자체)

---

- 정렬
    
    ```python
    # 오른쪽 정렬
    "%10s" % "hi"
    # 왼쪽 정렬은 %-10 
    ```
    
    → ‘          hi’
    
- 소수점 표현
    
    ```python
    # 소수 4번재 자리까지
    "%0.4f" % 3.42134234
    
    # 소수 4번째 자리까지 + 전체 길이 10, 오른쪽 정렬
    "%10.4f" % 3.42134234
    ```
    
    → '3.4213’   ,    ' 3.4213’
    
- format사용
    
    ```python
    "I eat {0} soup, {1} milk and {2} bananas".format(1,"two",3)
    ```
    
    → I eat 1 soup, two milk and 3 bananas
    
    ```python
    # 왼쪽 정렬
    "{0:<10}".format("hi")
    # 오른쪽 정렬
    "{0:>10}".format("hi")
    # 가운데 정렬
    "{0:^10}".format("hi")
    ```
    

## set

- 중복이 없는 데이터들의 집합
- 순서는 존재 / 대문자 - 소문자 순

```python
s = set([1,2,3,1,2])
s, type(s), len(s)
```

<aside>
🍒 ({1, 2, 3}, set, 3)

</aside>

- 문자를 입력하면??

```python
set("Hello")
```

<aside>
🍒 {'H', 'e', 'l', 'o'}

</aside>

- 값 추가 / 삭제

```python
s=set('Hello')
s.add('i')
s.discard('o')
```

<aside>
🍒 {'H', 'e', 'i', 'l'}

</aside>


### 리스트 컴프리헨션

- for-loop 반복문을 한 줄로 처리

```python
my_list = [[10],[20,30]]

flattened_list = []
for value_list in my_list:
  # print(value_list)
  for value in value_list:
    print(value)
    flattened_list.append(value)

print(flattened_list)
```

→ 리턴값 적어주고 위에서 하나씩 for문 써주면 된다.

```python
my_list = [[10],[20,30]]
flattened_list =[value for value_list in my_list for value in value_list]
print(flattened_list)
```




- list / tuple / set 비교

```python
x=[1,2,3,1,2,3]
list(x),tuple(x),set(x)
```

<aside>
🍒 ([1, 2, 3, 1, 2, 3], (1, 2, 3, 1, 2, 3), {1, 2, 3})

</aside>