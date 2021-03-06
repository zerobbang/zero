---
title: NiFi (WSL2)
date : "2022-04-13"
categories:
- [Setting]
---


๐ [์ฐธ๊ณ  ๋ธ๋ก๊ทธ](https://dschloe.github.io/settings/apache_nifi_wsl2/)  

  

- WSL2์ JAVA ์ค์น
    
    ```powershell
    $ sudo apt-get update && sudo apt-get upgrade
    $ sudo apt install openjdk-11-jre-headless
    $ vi ~/.bash_profile
    ```
    
    ๋ค์ ์ฝ๋ vi ํธ์ง๊ธฐ์ ์๋ ฅํ๋ค.
    
    ```powershell
    export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
    ```
    

  

- Nifi ๋ค์ด ๋ฐ๊ธฐ

    ```powershell
    sudo wget https://downloads.apache.org/nifi/1.16.0/nifi-1.16.0-bin.tar.gz
    ```

  

- ์์ถ ํ๊ธฐ

    ```powershell
    sudo tar xvzf nifi-1.16.0-bin.tar.gz
    ```

  

- nifi-1.16.0 ํด๋ ๋ค์ด๊ฐ๊ธฐ

    ```powershell
    cd nifi-1.16.0/bin
    ```

  

- nifi-env.sh ํด๋ โ ์๋ฐ ํ๊ฒฝ ๋ณ์ ์ก๊ธฐ

    ```powershell
    $ sudo vi nifi-env.sh
    export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
    ```

- nifi-env.sh ํ์ด ์คํ

    ```powershell
    sudo ./nifi.sh start
    
    Java home: /usr/lib/jvm/java-11-openjdk-amd64
    NiFi home: /nifi-1.16.0
    
    Bootstrap Config File: /nifi-1.16.0/conf/bootstrap.conf
    ```

  

- web ์ฃผ์ ํ์ธ โ conf ํ์ผ๋ก ๋ค์ด๊ฐ๊ธฐ
    
    ```powershell
    /nifi-1.16.0/conf$ cd .. 
    /nifi-1.16.0/conf$ vi nifi.properties
    ```
    
    ์ญ ๋ด๋ฆฌ๋ค ๋ณด๋ฉด ๋ค์๊ณผ ๊ฐ์ด host์ฃผ์์ port์ฃผ์๋ฅผ ์ฐพ์ ์ ์๋ค.
    
    ```powershell
    #############################################
    nifi.web.https.host=127.0.0.1
    nifi.web.https.port=8443
    ```
    
    โ NiFi ์ ์ ํ๊ธฐ [https://127.0.0.1:8443/nifi/](https://127.0.0.1:8443/nifi/)  
    
- ๋ก๊ทธ์ธ ํ๊ธฐ
    
    ๋ฐ๋ก ๋ก๊ทธ์ธ ํ๋ฉด username์ด ์๊ธฐ ๋๋ฌธ์ ๋ฐ๋ก ๋ก๊ทธ์ธ์ด ๋ถ๊ฐ๋ฅํ๋ค.  
    
    - ๋ณ๊ฒฝ ์ ์ logํ์ผ ์ง์์ฃผ๊ธฐ
        
        logs ํ์ผ ์ง์์ฃผ๊ธฐ
        
        ```powershell
        logs > sudo rm -rf *
        ```
        
    - ID, ๋น๋ฐ ๋ฒํธ ์ค์ 
        
        ```powershell
        sudo ./bin/nifi.sh set-single-user-credentials human 1234567890123
        ```
        
        human โ ์ ์  ๋ค์  
        1234567890123 โ ๋น๋ฐ๋ฒํธ  
        
    - ๋ค์ ์คํ ํ ๋ก๊ทธ์ธ
        
        ![](/images/nifi/Untitled.png)
        
    
      
---
**_<span style="color:#4682B4;"> ์ด ๋ธ๋ก๊ทธ๋ ํผ์ ๊ณต๋ถํ๋ฉฐ ๊ธฐ๋กํ๋ ๋ธ๋ก๊ทธ๋ก ์๋ชป๋ ์ ๋ณด์ ๋ํ ์๊ฒฌ์ ๊ฒฉํ๊ฒ ํ์ํฉ๋๋ค.๐คฉ </span>_**