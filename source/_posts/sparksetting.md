---
title: Hadoop Spark windows 10
date : "2022-04-19"
categories:
- [Setting]
---


๐ [์ฐธ๊ณ  ๋ธ๋ก๊ทธ](https://dschloe.github.io/python/python_edu/00_settings/spark_installation_windows_10/)  

  

## JAVA ์ค์น

Spark ์ค์น ํ๊ธฐ ์ ์ JAVA๊ฐ ์ค์น๋์ด ์์ด์ผ ํ๋ค.  

[๋ค์](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html)์ ํด๋ฆญํด์ ๋ค์ด๊ฐ ์ปดํจํฐ์ ๋ง๋ ๋ฒ์ ์ JAVA ์ค์น (ORACLE ๋ก๊ทธ์ธ ํ์)  

![](/images/sparksetting/Untitled.png)

  

- ๊ด๋ฆฌ์ ๊ถํ์ผ๋ก ์คํํด์ JAVA ์ค์น ์งํ
    
    ![](/images/sparksetting/Untitled%201.png)
    
     ๊ฒฝ๋ก์ ๊ณต๋ฐฑ์ด ์๋ ๊ฒฝ์ฐ ์ถํ์ ๋ฌธ์ ๊ฐ ์๊ธธ ์ ์๋ค. ๊ทธ๋์ c ๋๋ผ์ด๋ธ ์ ์๋ก ์์ฑํ jdk ํ์ผ๋ก ๊ฒฝ๋ก๋ฅผ ์ก์์ฃผ๊ณ  ์ค์น๋ฅผ ์งํํ๋ค. `c:\jdk`  
    
- ๋ฐํ์ ํ๊ฒฝ ํด๋๋ ๊ฒฝ๋ก๋ฅผ ๋ค์ ์ก์์ฃผ๊ณ  ์ค์น๋ฅผ ์งํ `c:\jre`
    
    ![](/images/sparksetting/Untitled%202.png)
    

  

---

## ์ค์นํ  ํ์ผ ๋ค์ด๋ก๋ ํ๊ธฐ

### Spark Download

- [Spark](https://spark.apache.org/downloads.html) ๋ค์ ํ์ด์ง๋ก ๋ค์ด๊ฐ์ Spark ํ์ผ์ ๋ค์ด ๋ฐ๋๋ค.
    
    ![](/images/sparksetting/Untitled%203.png)
    
- 3. Download Spark โ `spark-3.2.1-bin-hadoop3.2.tgz` ํด๋ฆญ
- **HTTP** ์๋์ ์๋ ๋งํฌ๋ฅผ ํตํด Spark ๋ค์ด ๋ฐ๋๋ค.
    
    ![](/images/sparksetting/Untitled%204.png)
    

  

- ๋ ๋ค๋ฅธ ๋ฐฉ๋ฒ (3.2.0 ๋ฒ์ )
    - [์ฌ๊ธฐ](https://www.apache.org/dyn/closer.lua/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz)๋ฅผ ํด๋ฆญํ์ฌ ๋ค์ด ๋ฐ๊ธฐ ( ๋ค์ ๊ทธ๋ฆผ์ ํ๋จ ๋งํฌ๋ก ๋ค์ด ์งํ)
    
    ![](/images/sparksetting/Untitled%205.png)
    

  

---

### WinRAR Download

- tgz ์์ถ ํ๊ธฐ ์ํด ํ์ํ **WinRAR** ์ค์น
    - [WinRAR](https://www.rarlab.com/download.htm)  : ๊ฐ์ธ ์ปดํจํฐ ์ฌ์์ ๋ง๋ ๋ฒ์ ์ผ๋ก ๋ค์ด๋ก๋
    
    ![](/images/sparksetting/Untitled%206.png)
    

  

---

### Winutils Download

- [์ฌ๊ธฐ](https://github.com/cdarlint/winutils)๋ฅผ ํด๋ฆญํ์ฌ Winutils ๋ค์ด ์งํ
    
    ![](/images/sparksetting/Untitled%207.png)
    
- ๋ค์ด ๋ฐ์ Spark์ ๋ฒ์ ๊ณผ ๋์ผํ ๋ฒ์ ์ ํด๋๋ฅผ ํด๋ฆญํ๋ค. ( 3.2.0 ๋ฒ์  )
    
    ![](/images/sparksetting/Untitled%208.png)
    
- ๋ค์ ํญ๋ชฉ์์ winutils.exe ๋ค์ด๋ก๋ ๋ฐ๊ธฐ
    
    ![](/images/sparksetting/Untitled%209.png)
    

  

---

## ์ค์น ํ๊ธฐ

 ์์์ ๋ค์ด ๋ฐ์ spark, winrar, java, winutils ํ์ผ์ c๋๋ผ์ด๋ธ ํ๋จ์ ์์ฑํ Hadoopํด๋๋ก ์ฎ๊ธด๋ค. (๋ค์ ์ฌ์ง์ spark ํ์ผ์ ๋ฌด์)  

![](/images/sparksetting/Untitled%2010.png)

  

1. WinRAR ๊ด๋ฆฌ์ ๊ถํ์ผ๋ก ์ค์น ์งํ
    - ๋ค์๊ณผ ๊ฐ์ด spark tgz ํ์ผ์ ์์ถ ํด์ ํ๋ค. `Extract to โspark-3.2.0-bin-hadoop3.2\โ`
        
        ![](/images/sparksetting/Untitled%2011.png)
        
2. ์์ถ ํด์ ํ ํ์ผ์ ๋ณต์ฌํ ํ c ๋๋ผ์ด๋ธ ํ๋จ์ sparkํด๋๋ก ์ ์ฅํ๋ค.
    
    ![](/images/sparksetting/Untitled%2012.png)
    
    - `conf`ํด๋๋ก ๋ค์ด๊ฐ `log4.properties` ํ์ผ์ ๋ค์๊ณผ ๊ฐ์ด ์์ ํ๋ค. ( INFO โ ERROR )
        
        ![](/images/sparksetting/Untitled%2013.png)
        
3. c ๋๋ผ์ด๋ธ ํ๋จ์ tmp ํด๋๋ฅผ ์์ฑํ๊ณ  ๊ทธ ์์ hive ํด๋๋ ์์ฑํ๋ค.
    
    ![](/images/sparksetting/Untitled%2014.png)
    
4. c ๋๋ผ์ด๋ธ ํ๋จ์ winutils ํด๋๋ฅผ ์์ฑํ๊ณ  bin ํด๋๋ฅผ ์์ฑ ํ ๊ทธ ์์ winutils๋ฅผ ๋ณต์ฌํ์ฌ ์ ์ฅํ๋ค.
    
    ![](/images/sparksetting/Untitled%2015.png)
    
    ์ด ํ์ผ์ spark ์คํ ํ  ๋ ์ค๋ฅ ์์ด ์คํ ๋๋๋ก ํ์ผ ์ฌ์ฉ ๊ถํ์ ์ป๋๋ก ํ๋ค.
    
    - cmd ๊ด๋ฆฌ์ ๊ถํ์ผ๋ก ์ด๊ธฐ
    - ๋ค์ ์ฝ๋๋ฅผ ์ฐจ๋ก๋๋ก ์๋ ฅํ๋ค.
        
        ```python
        cd c:\winutils\bin
        winutils.exe chmod 777 \tmp\hive
        ```
        

  

---

## ํ๊ฒฝ ๋ณ์ ์ค์ ํ๊ธฐ

- ์์คํ ํ๊ฒฝ ๋ณ์ ์ค์ 
- ์๋ก ๋ง๋ค๊ธฐ๋ก ๋ค์๊ณผ ๊ฐ์ด ์ถ๊ฐ ํด์ค๋ค. (๋ณ์ ๊ฐ ์ค์  ์ ๋ณต์ฌ ๋ถ์ด๊ธฐ๋ฅผ ์งํฅ)
    - JAVA_HOME
        
        ![](/images/sparksetting/Untitled%2016.png)
        
    - SPARK_HOME
        
        ![](/images/sparksetting/Untitled%2017.png)
        
    - HADOOP_HOME
        
        ![](/images/sparksetting/Untitled%2018.png)
        
    - PYSPARK_PYTHON
        
        ![](/images/sparksetting/Untitled%2019.png)
        
- ์ฌ์ฉ์ ๋ณ์์ Path ํธ์ง์ผ๋ก ๋ค์ด๊ฐ์ ๋ค์์ ์ถ๊ฐํ๊ธฐ
    - `%SPARK_HOME%\bin`
    - `%JAVA_HOME%\bin`
    
    ![](/images/sparksetting/Untitled%2020.png)
    

  

---

## Spark ํ์คํธ

- cmd ๊ด๋ฆฌ์ ๊ถํ์ผ๋ก ์คํ
- `c:\spark` ๊ฒฝ๋ก๋ก ๋ค์ด๊ฐ๊ธฐ
- pyspark ์คํ
    
    ![](/images/sparksetting/Untitled%2021.png)
    
- README.md ํ์ผ์ ๋ถ๋ฌ์์ ์ฝ๋๊ฐ ์คํ๋๋ ํ์ธ
    
    ```python
    >>> rd = sc.textFile("README.md")
    >>> rd.count()
    109
    ```
    
    ![](/images/sparksetting/Untitled%2022.png)

---
**_<span style="color:#4682B4;"> ์ด ๋ธ๋ก๊ทธ๋ ํผ์ ๊ณต๋ถํ๋ฉฐ ๊ธฐ๋กํ๋ ๋ธ๋ก๊ทธ๋ก ์๋ชป๋ ์ ๋ณด์ ๋ํ ์๊ฒฌ์ ๊ฒฉํ๊ฒ ํ์ํฉ๋๋ค.๐คฉ </span>_**