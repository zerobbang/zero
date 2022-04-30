---
title: Oracle sql plus 실행하기
date : "2022-04-25"
categories:
- [Sql]
tags:
- [Oracle]
---


### sql Plus 실행

![](/images/sqlplus/Untitled.png)

사용자명  :  system

비번 : 1234 

### 경로 설정

- 자신이 생성한 오라클 경로 확인 하기

```python
CREATE TABLESPACE myts DATAFILE 'C:\ocfile\oradata\MYORACLE\myts.dbf' SIZE 100M AUTOEXTEND ON NEXT 5M;
```

![](/images/sqlplus/Untitled%201.png)

![](/images/sqlplus/Untitled%202.png)

- 사용자 생성

```python
CREATE USER ora_user IDENTIFIED BY zero DEFAULT TABLESPACE MYTS TEMPORARY TABLESPACE TEMP;
```

다른거는 건드리지 말고 IDENTIFIED BY 다음을 바꿔주고 입력한다. 패스워드 

![](/images/sqlplus/Untitled%203.png)

나는 zero로 설정 ( 자신의 닉네임 )

- 롤 부여하기

![](/images/sqlplus/Untitled%204.png)

- 사용자 계정으로 DB 접속

![](/images/sqlplus/Untitled%205.png)


---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**