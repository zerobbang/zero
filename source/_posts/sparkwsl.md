---
title: Hadoop Spark in Linux (WSL2)
date : "2022-04-20"
categories:
- [Setting]
---


📎 [참고 블로그](https://dschloe.github.io/settings/spark_install_using_wsl/)  

이전 시간에 우리는 하둡 스파크를 윈도우 환경에서 세팅을 진행했다.  

이번에는 리눅스에서 진행하는 법을 살펴보자. 🍀  

  

### 사전 작업

Spark를 설치하기 전에 작업 할 환경을 설정해준다.  

  

1. 작업 파일 생성
2. pyspark 설치 및 경로 잡아주기
3. 실행

전체적인 흐름은 위와 같은데 우리는 window에서 설치 할 때 spark 다운을 받았기 때문에 다음 작업은 건너뛴다.    

- 작업 파일 생성

⇒ 여기에서 참고

### Linux에서 Spark Web UI 띄우기

이제 지난 시간에 spark를 설치한 폴더로 가기

`pwd`로 spark가 있는 경로 확인하고 기억한다.  

- ~/.bashrc 에서 다음과 같이 경로 잡아준다.

```powershell
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export SPARK_HOME=/mnt/c/spark
# 이 밑으로는 복사 붙여넣기 진행 ( 변경 되면 안되는 파트 )
export PATH=$JAVA_HOME/bin:$PATH
export PATH=$SPARK_HOME/bin:$PATH
export PYSPARK_PYTHON=/usr/bin/python3
```

만약에 JAVA와 Spark가 설치가 되어 있지 않다면 다음과 같이 설치하기

```powershell
$ sudo apt-get install openjdk-8-jdk
$ sudo wget https://archive.apache.org/dist/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz
# 압축 해제
$ sudo tar -xvzf spark-3.2.0-bin-hadoop3.2.tgz
```

그리고 경로 잡을 때 java 버전이랑 Spark가 있는 경로를 자신의 컴퓨터 환경에 맞게 바꿔서 잡아주어야 한다.  

경로를 다 잡아주었으면 bash파일을 업로드 `source ~/.bashrc` 해주고 pyspark를 실행한다.  

![](/images/sparkwsl/Untitled.png)

종료할 때는 `quit( )` 해주면 된다.  

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**