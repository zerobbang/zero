---
title: Airflow in Windows (WSL2)
date : "2022-04-13"
categories:
- [Setting]
---


📎 [참고 블로그](https://dschloe.github.io/settings/apache_airflow_using_wsl2/)  

  

- WSL 터미널에서 진행 (airflow_test 경로에서)
- WSL에 pip설치
    
    ```powershell
    sudo apt install python3-pip
    ```
    

---

  

- Virtualenv 라이브러리 설치
    
    ```powershell
    sudo pip3 install virtualenv
    ```
    

  

- 가상 환경 생성
    
    ```powershell
    virtualenv venv
    ```
    

  

- 가상 환경 접속
    
    ```powershell
    source venv/bin/activate
    ```
    

  

- .bashrc 파일 수정 ( vi 편집기 사용법 [참고](https://jhnyang.tistory.com/54) )
    
    ```powershell
    vi ~/.bashrc
    ```
    

  

- 파일 열고 다음 코드 추가 ( vi 편집기)
    
    ```powershell
    export AIRFLOW_HOME=/mnt/c/airflow-test # 폴더 경로
    ```
    
    [참고](https://jhnyang.tistory.com/54) 통해서 vi 편집기 저장한 후 나온다.
    

  

- 수정된 코드 업데이트
    
    ```powershell
    source ~/.bashrc
    ```
    

  

- 확인하기
    
    ```powershell
    & echo $AIRFLOW_HOME
    /mnt/c/airflow-test
    ```
    

  

---

### Apache Airflow 설치

venv 가상 환경에서 작업 수행   

- PostgreSQL, Slack, Celery 패키지 동시 설치
    
    ```powershell
    pip3 install 'apache-airflow[postgres, slack, celery]'
    ```
    

  

- Airflow 초기 실행 정 DB 초기화
    
    ```powershell
    airflow db init
    ```
    
    `Initialization done`
    

  

- 웹 서버 확인
    
    ```powershell
    airflow webserver -p 8081
    ```
    
    다음 링크로 들어가 확인하기. **[http://localhost:8081/login/](http://localhost:8081/login/)**
    
    ![](/images/airflow/Untitled.png)
    

    

- Username 생성
    
    ```powershell
    airflow users create --username airflow --password airflow --firstname evan --lastname airflow --role Admin --email your_email@some.com
    ```
    
    자신의 상황에 맞게 username과 password, name, email 입력하여 올린다.  
    
    그리고 다시 `webserver` 실행시키고 로그인하면 된다.  
    종료 : **ctrl c** (주의 ctrl z 하면 제대로 종료가 되지 않아서 좀비 프로세스가 된다.)
    
    ![](/images/airflow/Untitled%201.png)
    
    ![](/images/airflow/Untitled%202.png)
    
- Error - The webserver is already running under PID 숫자.
    - sudo kill -9 PID 숫자
    
    또는 ps -l 해서 확인
    
    [https://blog.daum.net/99lib/114](https://blog.daum.net/99lib/114)  
    
    [https://zetawiki.com/wiki/안_죽는_좀비_프로세스_죽이기](https://zetawiki.com/wiki/%EC%95%88_%EC%A3%BD%EB%8A%94_%EC%A2%80%EB%B9%84_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%A3%BD%EC%9D%B4%EA%B8%B0)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**