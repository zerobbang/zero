---
title: Python 기초 - Numpy
categories:
- [Python]
---

## list와 array 비교

```python
math_scores = [10,9,7]
eng_scores = [6,9,8]
math_arr = np.array(math_scores)
eng_arr = np.array(eng_scores)

total_scores = math_scores + eng_scores,  
total_arr = math_arr + eng_arr

total_scores, total_arr
```

- total_scores  → list
    
    <aside>
    🍒 ([10, 9, 7, 6, 9, 8])
    
    </aside>
    
- total_arr → array
    
    <aside>
    🍒 array([16, 18, 15])
    
    </aside>
    
- list 는 연산이 불가하고 numpy를 이용한 array는 가능하다.

## 사칙연산

```python
math_scores = [1,2,4]
eng_scores = [2,1,3]
math_arr = np.array(math_scores)
eng_arr = np.array(eng_scores)

print("덧셈 : ", np.add(math_arr,eng_arr))
print("뺄셈 : ", np.subtract(math_arr,eng_arr))
print("곱셈 : ",np.multiply(math_arr,eng_arr))
print("나눗셈 ", np.divide(math_arr,eng_arr))
print("거듭제곱 : ",np.power(math_arr,eng_arr))
```

- 결과
    
    <aside>
    🍒 덧셈 :  [3 3 7]
    뺄셈 :  [-1  1  1]
    곱셈 :  [ 2  2 12]
    나눗셈  [0.5        2.         1.33333333]
    거듭제곱 :  [ 1  2 64]
    
    </aside>
    
    → numpy의 연산 함수를 이용하여 간단하게 계산 가능
    

## 차원별 배열 생성

- 0차원
    
    ```python
    t_arr = np.array(20)
    print(t_arr,type(t_arr), t_arr.shape, t_arr.ndim)
    ```
    
    - 결과
        
        <aside>
        🍒 20 <class 'numpy.ndarray'> () 0
        
        </aside>
        
- 1차원
    
    ```python
    t_arr = np.array([1,2,3])
    print(t_arr,type(t_arr), t_arr.shape,t_arr.ndim)
    ```
    
    - 결과
        
        <aside>
        🍒 [1 2 3] <class 'numpy.ndarray'> (3,) 1
        
        </aside>
        
- 2차원
    
    ```python
    t_arr = np.array([[1,2],[3,4]])
    print(t_arr,type(t_arr), t_arr.shape,t_arr.ndim)
    ```
    
    - 결과
        
        <aside>
        🍒 [[1 2]
        [3 4]] <class 'numpy.ndarray'> (2, 2) 2
        
        </aside>
        
- 3차원
    
    ```python
    t_arr = np.array([[[1],[2]],[[3],[4]],[[5],[6]]])
    print(t_arr,type(t_arr), t_arr.shape,t_arr.ndim)
    ```
    
    - 결과
        
        <aside>
        🍒 [[[1]
        [2]] 
        
        [[3]
        [4]]
        
        [[5]
        [6]]] <class 'numpy.ndarray'> (3, 2, 1) 3
        
        </aside>
        
        - t_arr는 (2행, 1열)의 2차원 데이터가 3개가 있다.
- 차원 변경
    
    ```python
    # 1차원 -> 2차원
    t_arr = np.array([1,2,3,4],ndmin =2)
    print(t_arr,type(t_arr), t_arr.shape,t_arr.ndim)
    ```
    
    - 결과
        
        <aside>
        🍒 [[1 2 3 4]] <class 'numpy.ndarray'> (1, 4) 2
        
        </aside>
        

### (차원값, 행값, 열값) = axis 0, axis 1, axis 2

- 즉, axis 0 축을 따라서 배열이 쌓여있다고 생각
- axis 0에 따라 압축하면?

```python
print(np.sum(t_arr, axis=0))
```

<aside>
🍒 [[ 9]
[12]]

</aside>

→ axis 0 에따라 압축되어 
1행1열 = 1 + 3 + 5 = 9
1행 2열 = 2 + 4 + 6 = 12

- 참고 사이트
[https://steadiness-193.tistory.com/50](https://steadiness-193.tistory.com/50)

## 소수점 정리

```python
t_arr = ([-1.2, -1.6, 2.2, 2.5, 3.7])
```

- trunc 소수 버림
    
    ```python
    print(np.trunc(t_arr))
    ```
    
    <aside>
    🍒 [-1. -1. 2. 2. 3.]
    
    </aside>
    
- fix   0 방향으로 가장 가까운 정수로 내림 혹은 올림
    
    ```python
    print(np.fix(t_arr))
    ```
    
    <aside>
    🍒 [-1. -1. 2. 2. 3.]
    
    </aside>
    
- around, round 반올림
    
    ```python
    print(np.around(t_arr))
    print(np.round(t_arr))
    ```
    
    <aside>
    🍒 [-1. -2.  2.  2.  4.]
    [-1. -2.  2.  2.  4.]
    
    </aside>
    
- floor 내림
    
    ```python
    print(np.floor(t_arr)
    ```
    
    <aside>
    🍒 [-2. -2. 2. 2. 3.]
    
    </aside>
    
- ceil 올림
    
    ```python
    print(np.ceil(t_arr))
    ```
    
    <aside>
    🍒 [-1. -1. 3. 3. 4.]
    
    </aside>
    

## 자동으로 배열 생성

- arange ()
    
    ```python
    t_arr = np.arange(1,11,2)
    print(t_arr)
    ```
    
    - 결과
        
        <aside>
        🍒 [1 3 5 7 9]
        
        </aside>
        
- zeros
    
    ```python
    t_arr = np.zeros((2,4))
    print(t_arr)
    ```
    
    - 결과
        
        <aside>
        🍒 [[0. 0. 0. 0.]
        [0. 0. 0. 0.]]
        
        </aside>
        
- ones
    
    ```python
    t_arr = np.ones((3,3))
    print(t_arr)
    ```
    
    - 결과
        
        <aside>
        🍒 [[1. 1. 1.]
        [1. 1. 1.]
        [1. 1. 1.]]
        
        </aside>
        

## dtype

- 데이터 종류가 같아도 길이에 따라 오류 가능
- dtype 이용해 확인해 주기

```python
t_arr0 = np.ones((3,3))
t_arr1 = np.ones((3,3),dtype="int32")
print(t_arr0.dtype, t_arr.dtype1)
```

- 결과
    
    <aside>
    🍒 float64,  int32
    
    </aside>
    

## Reshape

```python
t_arr = np.ones((4,4),dtype = "int32")
t_re_arr = t_arr.reshape(2,-1)
# t_re_arr = t_arr.reshape(5,-1)   ->   cannot reshape array of size 16 into shape (5,newaxis)
print(t_arr,type(t_arr), t_arr.shape, t_arr.ndim,t_arr.dtype)
print(t_re_arr,type(t_re_arr), t_re_arr.shape, t_re_arr.ndim,t_re_arr.dtype)
```

- 결과
    
    <aside>
    🍒 [[1 1 1 1]
    [1 1 1 1]
    [1 1 1 1]
    [1 1 1 1]] <class 'numpy.ndarray'> (4, 4) 2 int32
    
    </aside>
    
    <aside>
    🍒 [[1 1 1 1 1 1 1 1]
    [1 1 1 1 1 1 1 1]] <class 'numpy.ndarray'> (2, 8) 2 int32
    
    </aside>
    
    → (4,4) 에서 (2,8)로 바꿔주었다.
    
    이 때 사이즈에 맞게 바꿔줘야 하는데 만약 2행으로 바꾸고 싶은데 열 사이즈를 모른다면 -1을 이용하여 자동으로 맞춰준다. (반대로도 가능)
    

## 조건식

- 조건 1 -  where ()
    
    ```python
    t_arr = np.arange(10)
    np.where(t_arr < 5, t_arr, t_arr * 10)
    ```
    
    - 결과
        
        <aside>
        🍒 array([ 0, 1, 2, 3, 4, 50, 60, 70, 80, 90])
        
        </aside>
        
- 조건 2개 이상
    
    ```python
    t_arr = np.arange(10)
    
    # 5 보다 큰 값 *2, 2 작은 값 + 100, 나머지 유지
    condlist = [t_arr > 5 , t_arr <2]
    choicelist = [t_arr *2, t_arr + 100]
    # np.select( cond, choice, default)
    print(t_arr)
    print(np.select(condlist, choicelist))
    print(np.select(condlist, choicelist, t_arr))
    ```
    
    - default 지정 X
        
        <aside>
        🍒 [0 1 2 3 4 5 6 7 8 9]
        [100 101 0 0 0 0 12 14 16 18]
        
        </aside>
        
    - default 지정 O
        
        <aside>
        🍒 [0 1 2 3 4 5 6 7 8 9]
        [100 101 2 3 4 5 12 14 16 18]
        
        </aside>