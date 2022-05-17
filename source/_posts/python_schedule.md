---
title: Python schedule 기초
date : "2022-05-17"
categories:
- [Python]
tags:
- [Python]
---

### 설치 하기

```bash
pip install schedule
```

### Schedule 함수 불러오기

```python
import schedule
```

### Schedule 함수 사용하기

**시간 단위**

```python
# 초 단위
schedule.every(10).seconds.do(함수이름)
# 분 단위
schedule.every(10).minutes.do(함수이름)
# 시 단위
schedule.every(10).hour.do(함수이름)
# 일 단위
schedule.every(10).days.do(함수이름)
# 주 단위
schedule.every(10).weeks.do(함수이름)
```

**원하는 타임 설정**

```python
schedule.every().day.at("13:00").do(함수이름)
# 초 단위까지 설정 가능
schedule.every().day.at("13:00:00").do(함수이름)

# 요일 설정 ( 소문자 입력 )
schedule.every().sunday.at("13:00").do(함수이름)
```

### Schedule 돌리기

```python
import schedule
import time

def test():
	print("Hi")

schedule.every(1).minutes.do(test)

# 무한 루프 중요
while True:
	schedule.run_pending()
	time.sleep(1)
```

[[참고]](https://coding-kindergarten.tistory.com/164)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**