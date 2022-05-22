---
title: heroku does not appear to be a git repo Error
date : "2022-05-22"
categories:
- [Error]
tags:
- [Error]
- [heroku]
---


```python
'heroku' does not appear to be a git repository
fatal: 'heroku' does not appear to be a git repository
fatal: Could not read from remote repository.
```

다른 컴퓨터에서 heroku를 작업하다가 집에 와서 개인 컴퓨터로 작업하려고 heroku를 돌렸는데 다음과 같은 에러 메세지가 떴다.  

이 에러가 나는 이유는 기존 컴퓨터와 heroku를 연결해주지 않아서 인데 이는 작업하는 환경을 바꾸게 되는 경우 꼭 다시 heroku를 잡아주어야 한다.  

```python
heroku git:remote -a (app이름)
```

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**