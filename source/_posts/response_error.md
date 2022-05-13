---
title: TypeError: 'Response' object is not subscriptable 에러
date : "2022-05-13"
categories:
- [Error]
tags:
- [OpenAPI]
---


open API를 처음 사용해보면서 값을 받아올 때 다음과 같은 에러와 마주했다.  

```bash
TypeError: 'Response' object is not subscriptable
```

Response는 open API에서 받아온 값의 집합인데 다음 [문서](https://docs.upbit.com/)를 통해서 해당 open API마다 불러들어와지는 Response를 살펴 볼 수 있다.  

위 에러가 난 이유는 타입 에러의 문제 였는데, 다음과 같이 그냥 바로 Response를 list나 dict과 같은 배열 형태로 생각하고 코드를 진행 했기 때문이다.  

```bash
url = "open API주소"
headers = {"Accept": "application/json"}

response = requests.get(url, headers=headers)
```

open API에서 주어지는 python 코드 그대로 가져온 후 response의 데이터를 다룰 때 바로 다루지 말고 `response.json()`과 같이 `json` 형태로 바꿔주어 데이터 전처리 작업을 진행해야한다.  

```bash
res = response.json()
```

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**