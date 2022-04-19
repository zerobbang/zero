---
title: Hadoop Spark windows 10
date : "2022-04-19"
categories:
- [Setting]
---


📎 [참고 블로그](https://dschloe.github.io/python/python_edu/00_settings/spark_installation_windows_10/)  

  

## JAVA 설치

Spark 설치 하기 전에 JAVA가 설치되어 있어야 한다.  

[다음](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html)을 클릭해서 들어가 컴퓨터에 맞는 버전의 JAVA 설치 (ORACLE 로그인 필수)  

![](/images/sparksetting/Untitled.png)

  

- 관리자 권한으로 실행해서 JAVA 설치 진행
    
    ![](/images/sparksetting/Untitled%201.png)
    
     경로에 공백이 있는 경우 추후에 문제가 생길 수 있다. 그래서 c 드라이브 안 새로 생성한 jdk 파일로 경로를 잡아주고 설치를 진행한다. `c:\jdk`  
    
- 런타임 환경 폴더도 경로를 다시 잡아주고 설치를 진행 `c:\jre`
    
    ![](/images/sparksetting/Untitled%202.png)
    

  

---

## 설치할 파일 다운로드 하기

### Spark Download

- [Spark](https://spark.apache.org/downloads.html) 다음 페이지로 들어가서 Spark 파일을 다운 받는다.
    
    ![](/images/sparksetting/Untitled%203.png)
    
- 3. Download Spark → `spark-3.2.1-bin-hadoop3.2.tgz` 클릭
- **HTTP** 아래에 있는 링크를 통해 Spark 다운 받는다.
    
    ![](/images/sparksetting/Untitled%204.png)
    

  

- 또 다른 방법 (3.2.0 버전)
    - [여기](https://www.apache.org/dyn/closer.lua/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz)를 클릭하여 다운 받기 ( 다음 그림의 하단 링크로 다운 진행)
    
    ![](/images/sparksetting/Untitled%205.png)
    

  

---

### WinRAR Download

- tgz 압축 풀기 위해 필요한 **WinRAR** 설치
    - [WinRAR](https://www.rarlab.com/download.htm)  : 개인 컴퓨터 사양에 맞는 버전으로 다운로드
    
    ![](/images/sparksetting/Untitled%206.png)
    

  

---

### Winutils Download

- [여기](https://github.com/cdarlint/winutils)를 클릭하여 Winutils 다운 진행
    
    ![](/images/sparksetting/Untitled%207.png)
    
- 다운 받은 Spark의 버전과 동일한 버전의 폴더를 클릭한다. ( 3.2.0 버전 )
    
    ![](/images/sparksetting/Untitled%208.png)
    
- 다음 항목에서 winutils.exe 다운로드 받기
    
    ![](/images/sparksetting/Untitled%209.png)
    

  

---

## 설치 하기

 위에서 다운 받은 spark, winrar, java, winutils 파일을 c드라이브 하단에 생성한 Hadoop폴더로 옮긴다. (다음 사진의 spark 파일은 무시)  

![](/images/sparksetting/Untitled%2010.png)

  

1. WinRAR 관리자 권한으로 설치 진행
    - 다음과 같이 spark tgz 파일을 압축 해제한다. `Extract to “spark-3.2.0-bin-hadoop3.2\”`
        
        ![](/images/sparksetting/Untitled%2011.png)
        
2. 압축 해제한 파일을 복사한 후 c 드라이브 하단에 spark폴더로 저장한다.
    
    ![](/images/sparksetting/Untitled%2012.png)
    
    - `conf`폴더로 들어가 `log4.properties` 파일을 다음과 같이 수정한다. ( INFO → ERROR )
        
        ![](/images/sparksetting/Untitled%2013.png)
        
3. c 드라이브 하단에 tmp 폴더를 생성하고 그 안에 hive 폴더도 생성한다.
    
    ![](/images/sparksetting/Untitled%2014.png)
    
4. c 드라이브 하단에 winutils 폴더를 생성하고 bin 폴더를 생성 후 그 안에 winutils를 복사하여 저장한다.
    
    ![](/images/sparksetting/Untitled%2015.png)
    
    이 파일은 spark 실행 할 때 오류 없이 실행 되도록 파일 사용 권한을 얻도록 한다.
    
    - cmd 관리자 권한으로 열기
    - 다음 코드를 차례대로 입력한다.
        
        ```python
        cd c:\winutils\bin
        winutils.exe chmod 777 \tmp\hive
        ```
        

  

---

## 환경 변수 설정하기

- 시스템 환경 변수 설정
- 새로 만들기로 다음과 같이 추가 해준다. (변수 값 설정 시 복사 붙이기를 지향)
    - JAVA_HOME
        
        ![](/images/sparksetting/Untitled%2016.png)
        
    - SPARK_HOME
        
        ![](/images/sparksetting/Untitled%2017.png)
        
    - HADOOP_HOME
        
        ![](/images/sparksetting/Untitled%2018.png)
        
    - PYSPARK_PYTHON
        
        ![](/images/sparksetting/Untitled%2019.png)
        
- 사용자 변수의 Path 편집으로 들어가서 다음을 추가하기
    - `%SPARK_HOME%\bin`
    - `%JAVA_HOME%\bin`
    
    ![](/images/sparksetting/Untitled%2020.png)
    

  

---

## Spark 테스트

- cmd 관리자 권한으로 실행
- `c:\spark` 경로로 들어가기
- pyspark 실행
    
    ![](/images/sparksetting/Untitled%2021.png)
    
- README.md 파일을 불러와서 코드가 실행되는 확인
    
    ```python
    >>> rd = sc.textFile("README.md")
    >>> rd.count()
    109
    ```
    
    ![](/images/sparksetting/Untitled%2022.png)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**