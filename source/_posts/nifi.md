---
title: NiFi (WSL2)
date : "2022-04-13"
categories:
- [Setting]
---


📎 [참고 블로그](https://dschloe.github.io/settings/apache_nifi_wsl2/)  

  

- WSL2에 JAVA 설치
    
    ```powershell
    $ sudo apt-get update && sudo apt-get upgrade
    $ sudo apt install openjdk-11-jre-headless
    $ vi ~/.bash_profile
    ```
    
    다음 코드 vi 편집기에 입력한다.
    
    ```powershell
    export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
    ```
    

  

- Nifi 다운 받기

    ```powershell
    sudo wget https://downloads.apache.org/nifi/1.16.0/nifi-1.16.0-bin.tar.gz
    ```

  

- 압축 풀기

    ```powershell
    sudo tar xvzf nifi-1.16.0-bin.tar.gz
    ```

  

- nifi-1.16.0 폴더 들어가기

    ```powershell
    cd nifi-1.16.0/bin
    ```

  

- nifi-env.sh 폴더 → 자바 환경 변수 잡기

    ```powershell
    $ sudo vi nifi-env.sh
    export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
    ```

- nifi-env.sh 파이 실행

    ```powershell
    sudo ./nifi.sh start
    
    Java home: /usr/lib/jvm/java-11-openjdk-amd64
    NiFi home: /nifi-1.16.0
    
    Bootstrap Config File: /nifi-1.16.0/conf/bootstrap.conf
    ```

  

- web 주소 확인 → conf 파일로 들어가기
    
    ```powershell
    /nifi-1.16.0/conf$ cd .. 
    /nifi-1.16.0/conf$ vi nifi.properties
    ```
    
    쭉 내리다 보면 다음과 같이 host주소와 port주소를 찾을 수 있다.
    
    ```powershell
    #############################################
    nifi.web.https.host=127.0.0.1
    nifi.web.https.port=8443
    ```
    
    → NiFi 접속 하기 [https://127.0.0.1:8443/nifi/](https://127.0.0.1:8443/nifi/)  
    
- 로그인 하기
    
    바로 로그인 하면 username이 없기 때문에 바로 로그인이 불가능하다.  
    
    - 변경 전에 log파일 지워주기
        
        logs 파일 지워주기
        
        ```powershell
        logs > sudo rm -rf *
        ```
        
    - ID, 비밀 번호 설정
        
        ```powershell
        sudo ./bin/nifi.sh set-single-user-credentials human 1234567890123
        ```
        
        human → 유저 네임  
        1234567890123 → 비밀번호  
        
    - 다시 실행 후 로그인
        
        ![](/images/nifi/Untitled.png)
        
    
      
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**