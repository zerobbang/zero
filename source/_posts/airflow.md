---
title: Airflow in Windows (WSL2)
date : "2022-04-13"
categories:
- [Setting]
---


๐ [์ฐธ๊ณ  ๋ธ๋ก๊ทธ](https://dschloe.github.io/settings/apache_airflow_using_wsl2/)  

  

- WSL ํฐ๋ฏธ๋์์ ์งํ (airflow_test ๊ฒฝ๋ก์์)
- WSL์ pip์ค์น
    
    ```powershell
    sudo apt install python3-pip
    ```
    

---

  

- Virtualenv ๋ผ์ด๋ธ๋ฌ๋ฆฌ ์ค์น
    
    ```powershell
    sudo pip3 install virtualenv
    ```
    

  

- ๊ฐ์ ํ๊ฒฝ ์์ฑ
    
    ```powershell
    virtualenv venv
    ```
    

  

- ๊ฐ์ ํ๊ฒฝ ์ ์
    
    ```powershell
    source venv/bin/activate
    ```
    

  

- .bashrc ํ์ผ ์์  ( vi ํธ์ง๊ธฐ ์ฌ์ฉ๋ฒ [์ฐธ๊ณ ](https://jhnyang.tistory.com/54) )
    
    ```powershell
    vi ~/.bashrc
    ```
    

  

- ํ์ผ ์ด๊ณ  ๋ค์ ์ฝ๋ ์ถ๊ฐ ( vi ํธ์ง๊ธฐ)
    
    ```powershell
    export AIRFLOW_HOME=/mnt/c/airflow-test # ํด๋ ๊ฒฝ๋ก
    ```
    
    [์ฐธ๊ณ ](https://jhnyang.tistory.com/54) ํตํด์ vi ํธ์ง๊ธฐ ์ ์ฅํ ํ ๋์จ๋ค.
    

  

- ์์ ๋ ์ฝ๋ ์๋ฐ์ดํธ
    
    ```powershell
    source ~/.bashrc
    ```
    

  

- ํ์ธํ๊ธฐ
    
    ```powershell
    & echo $AIRFLOW_HOME
    /mnt/c/airflow-test
    ```
    

  

---

### Apache Airflow ์ค์น

venv ๊ฐ์ ํ๊ฒฝ์์ ์์ ์ํ   

- PostgreSQL, Slack, Celery ํจํค์ง ๋์ ์ค์น
    
    ```powershell
    pip3 install 'apache-airflow[postgres, slack, celery]'
    ```
    

  

- Airflow ์ด๊ธฐ ์คํ ์  DB ์ด๊ธฐํ
    
    ```powershell
    airflow db init
    ```
    
    `Initialization done`
    

  

- ์น ์๋ฒ ํ์ธ
    
    ```powershell
    airflow webserver -p 8081
    ```
    
    ๋ค์ ๋งํฌ๋ก ๋ค์ด๊ฐ ํ์ธํ๊ธฐ. **[http://localhost:8081/login/](http://localhost:8081/login/)**
    
    ![](/images/airflow/Untitled.png)
    

    

- Username ์์ฑ
    
    ```powershell
    airflow users create --username airflow --password airflow --firstname evan --lastname airflow --role Admin --email your_email@some.com
    ```
    
    ์์ ์ ์ํฉ์ ๋ง๊ฒ username๊ณผ password, name, email ์๋ ฅํ์ฌ ์ฌ๋ฆฐ๋ค.  
    
    ๊ทธ๋ฆฌ๊ณ  ๋ค์ `webserver` ์คํ์ํค๊ณ  ๋ก๊ทธ์ธํ๋ฉด ๋๋ค.  
    ์ข๋ฃ : **ctrl c** (์ฃผ์ ctrl z ํ๋ฉด ์ ๋๋ก ์ข๋ฃ๊ฐ ๋์ง ์์์ ์ข๋น ํ๋ก์ธ์ค๊ฐ ๋๋ค.)
    
    ![](/images/airflow/Untitled%201.png)
    
    ![](/images/airflow/Untitled%202.png)
    
- Error - The webserver is already running under PID ์ซ์.
    - sudo kill -9 PID ์ซ์
    
    ๋๋ ps -l ํด์ ํ์ธ
    
    [https://blog.daum.net/99lib/114](https://blog.daum.net/99lib/114)  
    
    [https://zetawiki.com/wiki/์_์ฃฝ๋_์ข๋น_ํ๋ก์ธ์ค_์ฃฝ์ด๊ธฐ](https://zetawiki.com/wiki/%EC%95%88_%EC%A3%BD%EB%8A%94_%EC%A2%80%EB%B9%84_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%A3%BD%EC%9D%B4%EA%B8%B0)

---
**_<span style="color:#4682B4;"> ์ด ๋ธ๋ก๊ทธ๋ ํผ์ ๊ณต๋ถํ๋ฉฐ ๊ธฐ๋กํ๋ ๋ธ๋ก๊ทธ๋ก ์๋ชป๋ ์ ๋ณด์ ๋ํ ์๊ฒฌ์ ๊ฒฉํ๊ฒ ํ์ํฉ๋๋ค.๐คฉ </span>_**