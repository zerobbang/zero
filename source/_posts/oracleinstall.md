---
title: Oracle 설치
date : "2022-04-25"
categories:
- [Sql]
tags:
- [Oracle]
---


**orcale database 19c** 버전으로 설치를 진행한다.  

### Download

[Oracle 다운](https://www.oracle.com/kr/database/technologies/oracle19c-windows-downloads.html)  

[SQL developer 다운](https://www.oracle.com/kr/database/technologies/appdev/sqldeveloper-landing.html)

SQL  developer 는  java 사용하기 때문에 다음 버전을 다운로드 한다.  

![](/images/oracleinstall/Untitled.png)

- 다운로드 받은 2개의 파일을 C 하단 파일로 옮긴다. ( 새로운 폴더 생성 )

  

---

## Install

- WINDOWS.X64_193000_db_home → setUP 관리자 권한으로 실행
- 단일 인스턴스 데이터 베이스 생성 및 구성 선택 → 다음

![](/images/oracleinstall/Untitled%201.png)

- 데스크톱 클래스 → 다음

![](/images/oracleinstall/Untitled%202.png)

- 가상 계정 사용 → 다음

![](/images/oracleinstall/Untitled%203.png)

- 다음과 같이 전역 데이터베이스 이름 설정 및 비밀번호 설정하고 **컨테이너 데이터베이스로 생성** 체크 풀어주기

![](/images/oracleinstall/Untitled%204.png)

※ 다음과 같이 error가 발생했다.  ( 자세한 이유는 모르지만 개인 pc가 아니라서 생긴 문제일 수 있음. )

![](/images/oracleinstall/Untitled%205.png)

- 다시 처음으로 돌아가 **소프트웨어만 설정**으로 진행. → 추후에 db 생성을 따로 해줘야 한다.

![](/images/oracleinstall/Untitled%206.png)

- 단일 인스턴스 데이터베이스 설치 → 다음

![](/images/oracleinstall/Untitled%207.png)

- Enterprise Edition → 다음

![](/images/oracleinstall/Untitled%208.png)

- 가상 계정 사용 → 다음

![](/images/oracleinstall/Untitled%209.png)

- 다음

![](/images/oracleinstall/Untitled%2010.png)

- 완료 되면 설치 클릭

![](/images/oracleinstall/Untitled%2011.png)

![](/images/oracleinstall/Untitled%2012.png)

![](/images/oracleinstall/Untitled%2013.png)

  

### DB 설정

- 따로 DB 설정하기 → 소프트웨어만 설치하기 했을 경우
- 전역 데이터베이스 설정되어 있지 않음.
- Oracle - OraDB19Home1 파일 생성 확인하기
    
    ![](/images/oracleinstall/Untitled%2014.png)
    
- cmd → oracle 다운 받은 파일로 이동 → dir 로 파일 확인 해주기
    
    ![](/images/oracleinstall/Untitled%2015.png)
    
- `dbca`  입력해서 DB 생성 시작

![](/images/oracleinstall/Untitled%2016.png)

- 다음과 같이 설정해주고 다음 클릭한다.
- 저장 영역 유형을 ASM으로 하고 db 파일 위치랑 FRA를 다음과 같이 입력하고 다음 눌렀을 때 또 에러가 발생하면  저장 영역 유형을 파일 시스템으로 변경 후 진행한다.

![](/images/oracleinstall/Untitled%2017.png)

![](/images/oracleinstall/Untitled%2018.png)

- 다음 경고 창은 큰 상관이 없으므로 예를 눌러서 계속 진행한다.

![](/images/oracleinstall/Untitled%2019.png)

- 완료를 눌러주고 설치가 다 완료 되면 닫기를 눌러 설치를 마친다.

![](/images/oracleinstall/Untitled%2020.png)

![](/images/oracleinstall/Untitled%2021.png)

- 만약에 cmd에서 들어가서 하는 방법도 에러가 나면 다음으로 들어가 위와 같은 방법으로 진행해본다.
    
    ![](/images/oracleinstall/Untitled%2022.png)
    

  

지금까지 문제 없이 잘 설치가 되었다면 끝난 것이다.  
만약 설치 중에 취소 했다가 다시 진행하거나 설치 중에 오류가 발생해서 다시 설치를 진행해야 한다면 다시 설치 진행을 하기 보다는 기존 Oracle 삭제하고 **다시 처음부터 진행**하는 것을 권장한다.


  

Oracle 삭제 방법은 다음 블로그를 참고.
[Oracle 삭제하기](https://dschloe.github.io/sql/oracle_deinstallation/)
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**