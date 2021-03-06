---
title: Hadoop Spark in Linux (WSL2)
date : "2022-04-20"
categories:
- [Setting]
---


๐ [์ฐธ๊ณ  ๋ธ๋ก๊ทธ](https://dschloe.github.io/settings/spark_install_using_wsl/)  

์ด์  ์๊ฐ์ ์ฐ๋ฆฌ๋ ํ๋ก ์คํํฌ๋ฅผ ์๋์ฐ ํ๊ฒฝ์์ ์ธํ์ ์งํํ๋ค.  

์ด๋ฒ์๋ ๋ฆฌ๋์ค์์ ์งํํ๋ ๋ฒ์ ์ดํด๋ณด์. ๐  

  

### ์ฌ์  ์์

Spark๋ฅผ ์ค์นํ๊ธฐ ์ ์ ์์ ํ  ํ๊ฒฝ์ ์ค์ ํด์ค๋ค.  

  

1. ์์ ํ์ผ ์์ฑ
2. pyspark ์ค์น ๋ฐ ๊ฒฝ๋ก ์ก์์ฃผ๊ธฐ
3. ์คํ

์ ์ฒด์ ์ธ ํ๋ฆ์ ์์ ๊ฐ์๋ฐ ์ฐ๋ฆฌ๋ window์์ ์ค์น ํ  ๋ spark ๋ค์ด์ ๋ฐ์๊ธฐ ๋๋ฌธ์ ๋ค์ ์์์ ๊ฑด๋๋ด๋ค.  
โ ์ฌ๊ธฐ์์ [์ฐธ๊ณ ](https://zerobbang.github.io/2022/04/19/sparksetting/)

### Linux์์ Spark Web UI ๋์ฐ๊ธฐ

์ด์  ์ง๋ ์๊ฐ์ spark๋ฅผ ์ค์นํ ํด๋๋ก ๊ฐ๊ธฐ

`pwd`๋ก spark๊ฐ ์๋ ๊ฒฝ๋ก ํ์ธํ๊ณ  ๊ธฐ์ตํ๋ค.  

- ~/.bashrc ์์ ๋ค์๊ณผ ๊ฐ์ด ๊ฒฝ๋ก ์ก์์ค๋ค.

```powershell
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export SPARK_HOME=/mnt/c/spark
# ์ด ๋ฐ์ผ๋ก๋ ๋ณต์ฌ ๋ถ์ฌ๋ฃ๊ธฐ ์งํ ( ๋ณ๊ฒฝ ๋๋ฉด ์๋๋ ํํธ )
export PATH=$JAVA_HOME/bin:$PATH
export PATH=$SPARK_HOME/bin:$PATH
export PYSPARK_PYTHON=/usr/bin/python3
```

๋ง์ฝ์ JAVA์ Spark๊ฐ ์ค์น๊ฐ ๋์ด ์์ง ์๋ค๋ฉด ๋ค์๊ณผ ๊ฐ์ด ์ค์นํ๊ธฐ

```powershell
$ sudo apt-get install openjdk-8-jdk
$ sudo wget https://archive.apache.org/dist/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz
# ์์ถ ํด์ 
$ sudo tar -xvzf spark-3.2.0-bin-hadoop3.2.tgz
```

๊ทธ๋ฆฌ๊ณ  ๊ฒฝ๋ก ์ก์ ๋ java ๋ฒ์ ์ด๋ Spark๊ฐ ์๋ ๊ฒฝ๋ก๋ฅผ ์์ ์ ์ปดํจํฐ ํ๊ฒฝ์ ๋ง๊ฒ ๋ฐ๊ฟ์ ์ก์์ฃผ์ด์ผ ํ๋ค.  

๊ฒฝ๋ก๋ฅผ ๋ค ์ก์์ฃผ์์ผ๋ฉด bashํ์ผ์ ์๋ก๋ `source ~/.bashrc` ํด์ฃผ๊ณ  pyspark๋ฅผ ์คํํ๋ค.  

![](/images/sparkwsl/Untitled.png)

์ข๋ฃํ  ๋๋ `quit( )` ํด์ฃผ๋ฉด ๋๋ค.  

---
**_<span style="color:#4682B4;"> ์ด ๋ธ๋ก๊ทธ๋ ํผ์ ๊ณต๋ถํ๋ฉฐ ๊ธฐ๋กํ๋ ๋ธ๋ก๊ทธ๋ก ์๋ชป๋ ์ ๋ณด์ ๋ํ ์๊ฒฌ์ ๊ฒฉํ๊ฒ ํ์ํฉ๋๋ค.๐คฉ </span>_**