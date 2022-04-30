---
title: SQL Developer 설치
date : "2022-04-25"
categories:
- [Sql]
tags:
- [Oracle]
---


### SQL Developer Install

[이전](https://zerobbang.github.io/2022/04/25/oracleinstall/)에서 다운 받은 SQL Developer 압축 파일을 해제한 후 sqldeveloper 실행  

![](/images/sqldevinstall/Untitled.png)

다음과 같은 경고 창이 나오면 아니요 누른 후에 계속 진행한다.  
( 만약 JAVA 환경 설정이 되어 있지 않으면 잡아줘야 한다. )  

![](/images/sqldevinstall/Untitled%201.png)

- 정상적으로 실행되면 다음과 같은 화면이 나온다. 여기에서 + 클릭해서 새 데이터베이스 접속으로 들어가기

![](/images/sqldevinstall/Untitled%202.png)

![](/images/sqldevinstall/Untitled%203.png)

- Name과 사용자 이름을 이전에서 설치한 것과 동일하게 ora_user로 설정해주고 SID에 myoracle 입력해주고 테스트를 실행해본다.
- 비밀번호는 이전 Oracle 설치 시 자신의 닉네임 ( 나의 경우 zero ) 으로 하면 된다.

![](/images/sqldevinstall/Untitled%204.png)

  

  

- **실패 - 테스트 실패 : IO 오류 발생 → cmd → lsnrctl status 입력**

![](/images/sqldevinstall/Untitled%205.png)

위 사진처럼 출력이 되는 경우 리스너 문제이다. 다음을 따라해서 리스너 잡아주기  

![](/images/sqldevinstall/Untitled%206.png)

- Net Configuration Assistant 실행 -  설정 건드리지 말고 계속 설치하여 다음과 같이 나오면 된다.

![](/images/sqldevinstall/Untitled%207.png)

- Oracle 로 다시 돌아가서 테스트 후 접속 하면 다음과 같이 성공

![](/images/sqldevinstall/Untitled%208.png)

  

### Oracle 초기 설정

- 도구 → 환경설정

![](/images/sqldevinstall/Untitled%209.png)

![](/images/sqldevinstall/Untitled%2010.png)

- 데이터베이스 → NLS → 시간 기록 형식을 다음과 같이 변경 후 확인

> 시간 기록 형식 : YYYY/MM/DD HH24:MI:SS
> 
- 제대로 작동하는지 확인

```powershell
SELECT user from DUAL;
-> ORA_USER 나오면 성공
```

![](/images/sqldevinstall/Untitled%2011.png)

  

  

---

### Sample Schema 실행

참고서 : [Oracle](http://www.kyobobook.co.kr/product/detailViewKor.laf?mallGb=KOR&ejkGb=KOR&barcode=9788966189984)  

- [다음](https://github.com/gilbutITbook/006696/tree/master/01%EC%9E%A5%20%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95) 링크로 가서 밑에 2개 다운
    - expall.dmp
    - expcust.dmp

![](/images/sqldevinstall/Untitled%2012.png)

  

- C드라이브 밑에 backup 폴더 생성 후 위에서 다운 받은 2개의 파일을 옮겨 놓는다.

![](/images/sqldevinstall/Untitled%2013.png)

  

- cmd에서 backup 파일로 들어가서 다음을 실행

여기서 imp ora_user/( 앞에서 설정한 자신의 닉네임  ) 으로 변경해서 입력해준다.  

```powershell
imp ora_user/zero file=expall.dmp log=empall.log ignore=y grants=y rows=y indexes=y full=y

```

```powershell
imp ora_user/zero file=expcust.dmp log=expcust.log ignore=y grants=y rows=y indexes=y full=y
```

![](/images/sqldevinstall/Untitled%2014.png)

![](/images/sqldevinstall/Untitled%2015.png)

  

- 다시 Oracle로 돌아가서 다음 코드를 실행

```powershell
SELECT table_name FROM user_tables;
```

![](/images/sqldevinstall/Untitled%2016.png)

위와 같이 10개의 테이블 이름이 출력이 된다면 정상적으로 설치가 된 것이다.  

- 앞으로는 다음과 같이 접속하면 된다.

![](/images/sqldevinstall/Untitled%2017.png)


---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**