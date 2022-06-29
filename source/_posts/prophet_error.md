---
title: Python ARIMA & fbprophet 설치 오류
date : "2022-05-10"
categories:
- [Error]
tags:
- [Arima]
- [fbprophet]
---


### ARIMA 설치

```bash
pip install statsmodels
```

### Facebook prophet

```bash
pip install cython
pip install "pystan<2.18"
pip install fbprophet
```

facdbook prophet을 사용하기 위해 차례대로 cython과 pystan을 설치해주었다.  
cython을 설치가 정상적으로 잘 되었는데 pystan 설치가 다음과 같이 에러가 뜨면서 설치를 완료하지 못했다.  

![](/images/prophet_error/Untitled.png)

에러 구글링 해보면서 원인을 찾아보고 있는데 아직 해결 방법을 찾지 못했다.

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**