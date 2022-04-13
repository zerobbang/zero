---
title: PostgreSQL (WSL2)
date : "2022-04-13"
categories:
- [Setting]
---

📎 [참고 블로그](https://dschloe.github.io/sql/postgreslq_wsl2/)  

  

- WSL 터미널에서 진행
- Ubuntu 패키지 업데이트 및 업그레이드 진행

    ```powershell
    sudo apt-get update && sudo apt-get upgrade
    ```
    
    ---

  

- PostgreSQL 설치

    ```powershell
    sudo apt install postgresql postgresql-contrib
    
    # 버전 확인
    psql --version
    ```

- DB에 접근 가능하도록 활성화

    ```powershell
    # 상태 확인
    sudo service postgresql status
    
    # 활성화
    sudo service postgresql start
    
    # 종료
    sudo service postgresql stop
    ```

- 사용자 계정 설정

    ```powershell
    sudo passwd postgres
    ```

---

   

### pgAdmin 설치

- [pgAdmin](https://www.pgadmin.org/download/pgadmin-4-windows/) → 최신 버전 pgAdmin 4 v6.8
- 설치 시 관리자로 실행 및 **install for all users**로 설치 진행
- 서버 설정하기
    - Servers → Register → Server...
    
    ![](/images/PostgreSQL/Untitled.png)
    
    - General Tab → test
        
        ![](/images/PostgreSQL/Untitled%201.png)
        
    - Connection → Password 입력, Host name 127.0.0.1
        
        ![](/images/PostgreSQL/Untitled%202.png)
        
        만약 에러가 난다면 다음과 같이 진행한다.  
          
        service 활성화된 상태에서 다음 코드 입력
        
        ```powershell
        $ sudo -u postgres psql -c "ALTER USER postgres PASSWORD '<new-password>';"
        ```
        
        new-password 에 자신의 비밀 번호 입력  
          
        다시 바꾼 비밀번호 입력하고 save
        
        ![](/images/PostgreSQL/Untitled%203.png)
        

  

### DB 생성 및 확인

- Database 우클릭 → Create

![](/images/PostgreSQL/Untitled%204.png)

![](/images/PostgreSQL/Untitled%205.png)

- dataengineering 노드 → shemas → public → Tables 우클릭 → Create - Table 선택
    - General 다음과 같이 설정
        
        ![](/images/PostgreSQL/Untitled%206.png)
        
    - Columns 다음과 같이 설정
        
        ![](/images/PostgreSQL/Untitled%207.png)
        

### psql 에서 쿼리 실행

- psql 실행하면 다음과 같이 된다.
    
    ```powershell
    $ sudo -u postgres psql
    psql (12.9 (Ubuntu 12.9-0ubuntu0.20.04.1))
    Type "help" for help.
    
    postgres=#
    ```
    
- DB 조회

    ```powershell
    postgres=# \l
    
    List of databases
          Name       |  Owner   | Encoding | Collate |  Ctype  |   Access privileges
    -----------------+----------+----------+---------+---------+-----------------------
     dataengineering | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
     postgres        | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
     template0       | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
                     |          |          |         |         | postgres=CTc/postgres
     template1       | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres          +
                     |          |          |         |         | postgres=CTc/postgres
    (4 rows)
    ```

- DB 연결 후 테이블 조회

    ```powershell
    postgres=# \c dataengineering
    You are now connected to database "dataengineering" as user "postgres".
    
    dataengineering=# \dt
             List of relations
     Schema | Name  | Type  |  Owner
    --------+-------+-------+----------
     public | users | table | postgres
    ```


---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**