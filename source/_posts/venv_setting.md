---
title: Python - 가상 환경 생성 (PyCharm)
date : "2022-03-28"
categories:
- [Python]
---

이번에는 PyCharm 통해서 가상 환경 설정하는 법을 알아보려 한다.

### 가상 환경이 왜 필요한가

 우선 가상 환경을 설정하기 전에 가상 환경이 왜 필요한지 알아보면 다음과 같다.

 예를 들어 파이썬 기본 엔진을 통해서 파이썬의 버전이 다른 웹 2개를 생성했는데 동일한 라이브러리가 필요하다면 에러가 발생할 수 있다.

 그 이유는 버전이 다른 파이썬에서 동일한 라이브러리를 불러오게 되면 두 웹에서는 각각 다른 버전의 라이브러리를 필요로 하는데 한 환경에서 라이브러리는 하나의 버전만 갖고 있을 수 있기 때문이다.

## 가상 환경 설정하기

- PyCharm에서 새로운 프로젝트를 생성하는데 다음과 같이 생성해준다.
- (사진)
- 새로운  프로젝트가 생성이 되었으면 가상 환경이 잘 생성되었는지 다음 코드를 입력하여 확인한다.
    
    ```python
    which python
    ```
    
    ![Untitled](/images/venv_setting/Untitled.png)
    
    위 에서 보는 것처럼 가상 환경이 잘 생성되었다면 /(파일명)/ venv/Scripts/python 을 확인 할 수 있다.
    

- 생성이 안되어 있다면 다음과 같이 직접 입력하여 생성한다.

```python
source venv/Scripts/activate
```

- 가상환경이 생성되었다면 기본 코드를 실행해보자.
    
    ![Untitled](/images/venv_setting/Untitled%201.png)
    
    Hi, PyCharm을 프린트하는 코드가 잘 실행되었다.
    

- 버전 충돌을 막기위해 가상환경을 생성 했기 때문에 새로 환경을 만들 때마다 필요한 라이브럴리를 다운받아줘야 한다.
- 다운 받지 않고 그냥 실행 할 경우 다음과 같은 에러가 발생한다.
    
    ```
    ModuleNotFoundError: No moduled named 'numpy’
    ```
    
- 다음과 같은 방법으로 필요 라이브러리를 설치하여 사용
    
    ```python
    pip install numpy
    ```
    
- main.py 코드
    
    ```python
    import numpy as np
    
    def print_hi(name):
        # Use a breakpoint in the code line below to debug your script.
        print(f'Hi, {name}')  # Press Ctrl+F8 to toggle the breakpoint.
    
    if __name__ == '__main__':
        print_hi('PyCharm')
        print("numpy version : ", np.__version__)
    ```
    
- 잘 설치 되면 다음과 같이 잘 실행된다.
    
    ```python
    $ python [main.py](http://main.py/)
    Hi, PyCharm
    numpy version :  1.22.3
    ```
    

- 라이브러리 설치 확인하는 또 다른 방법
    
    /venv/Lib들어가면 해당 가상환경에서 설치한 라이브러리들을 확인 가능하다.
    
    ![Untitled](/images/venv_setting/Untitled%202.png)