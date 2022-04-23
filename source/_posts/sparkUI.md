---
title: Spark Web Ui 생성하기
date : "2022-04-23"
categories:
- [Setting]
---


VSCode에서 실습  

- 작업할 폴더 생성
    
    ```python
    mkdir 폴더 이름
    ```
    
    ![](/images/sparkUI/Untitled.png)
    
    나는 pys_pro 이름으로 c 드라이브 하단에 생성.  
    
- window에서 가상 환경 설정하기 ( 필수 작업 )
    
    ```python
    # 가상 환경 설치
    pip3 install virtualenv
    
    # 가상 환경 생성
    virtualenv venv
    
    # 가상 환경 실행 (Windows)
    source venv/Scripts/activate  
    ```
    
    ![](/images/sparkUI/Untitled%201.png)
    

  

---

### Spark web UI

- SparkSession?
 모든 스파크 Application은 가장 먼저 SparkSession 생성 하는데 이는 Spark의 기능들을 사용할 수 있도록 해주는 매개체이며 DataFrame과 DataSet APIs 사용하여 Spark 사용할 수 있도록 해준다.  
상용구 코드 —  .bulider  /  .appName()  /  .getOrCreate()

- SparkContext?
SparkContext를 통해 data를 RDD 형태로 변환을 가능하게 한다.

- SparkConf?
 SparkContext에 적용되는 필요한 설정들을 지정한다.  
상용구 코드 —  .setMaster()  /  .setAppName()

- 라이브러리 불러오기
    
    ```python
    from pyspark.sql import SparkSession
    from pyspark import SparkConf, SparkContext
    import pyspark
    # 버전 확인 
    # print(pyspark.__version__)
    ```
    

- 스파크 session 초기화
    
    ```python
    spark = SparkSession.builder.master('local[1]').appName('SampleTutorial').getOrCreate()
    conf = SparkConf().setMaster('local').setAppName('FirstSpark')
    sc = SparkContext(conf = conf)
    ```
    
    스파크 클러스터의 마스터 노드와 appName을 지정하면서 스파크 세션 객체 생성한다.  
    
    Spark Web UI (localhost:4040) 로 가면 Running Applications에서 Name이 `SampleTutorial`인 Application을 확인 할 수 있다.  
    

- 스파크 중지
    
    ```python
    spark.stop()
    ```
    

  

- 전체 기본 코드
    
    ```python
    # -*- coding: utf-8 -*- 
    
    import pyspark
    print(pyspark.__version__)
    
    from pyspark.sql import SparkSession
    
    # 스파크 세션 초기화
    spark = SparkSession.builder.master('local[1]').appName('SampleTutorial').getOrCreate()
    conf = SparkConf().setMaster('local').setAppName('FirstSpark')
    sc = SparkContext(conf = conf)
    
    # 스파크 중지
    spark.stop()
    ```
    

  

- pysaprk 없으면 설치한다. `pip install pyspark`

Spark를 이용하기 위해 사전 작업은 끝났다.  

  

---

### UI 불러오기 - Linux

다음 사이트 참고 [Spark](https://spark.apache.org/docs/latest/quick-start.html)  

![](/images/sparkUI/Untitled%202.png)

  

  

- 새로운 작업 환경 생성
    
    ```powershell
    $ mkdir 폴더 이름
    $ cd 폴더 이름
    
    # 가상 환경 생성
    $ virtualenv venv
    $ source venv/bin/activate
    
    # install pyspark
    $ pip install pyspark
    ```
    
- 작업 파일 생성
    
    ```powershell
    $ vi simpleApp
    ```
    
- 예제 코드 작성
    
    ```powershell
    """SimpleApp.py"""
    from pyspark.sql import SparkSession
    
    logFile = "YOUR_SPARK_HOME/README.md"  # Should be some file on your system
    spark = SparkSession.builder.appName("SimpleApp").getOrCreate()
    logData = spark.read.text(logFile).cache()
    
    numAs = logData.filter(logData.value.contains('a')).count()
    numBs = logData.filter(logData.value.contains('b')).count()
    
    print("Lines with a: %i, lines with b: %i" % (numAs, numBs))
    
    spark.stop()
    ```
    
    이대로 돌리게 되면 spark server가 바로 다운 되기 때문에 잘 작동하는지 확인 할 수 가 없다.  
    
    그래서 input 문을 사용하여 서버가 다운 되지 않고 계속 돌아가도록 작동하게 만든다. (일종의 트릭)  
    
    ```powershell
    from pyspark.sql import SparkSession
    
    logFile = "data/README.md"  # Should be some file on your system
    spark = SparkSession.builder.appName("SimpleApp").getOrCreate()
    logData = spark.read.text(logFile).cache()
    
    numAs = logData.filter(logData.value.contains('a')).count()
    numBs = logData.filter(logData.value.contains('b')).count()
    
    print("Lines with a: %i, lines with b: %i" % (numAs, numBs))
    
    # 추가된 코드
    input("Typing....")
    
    spark.stop()
    ```
    
- README.md 파일 생성
    - 위 예제 코드에서 README.md 파일을 불러와 프로그램을 돌리기 때문에 이에 맞춰서 우리도 같이 생성해준다.
    - 작업 파일 생성한 곳에서 하위 폴더를 생성하고 그 안에 [README.md](http://README.md) 파일 생성 후 다음 스크립트 복사 붙이기.
    
    > This program just counts the number of lines containing ‘a’ and the number containing ‘b’ in a text file. Note that you’ll need to replace YOUR_SPARK_HOME with the location where Spark is installed. As with the Scala and Java examples, we use a SparkSession to create Datasets. For applications that use custom classes or third-party libraries, we can also add code dependencies to `spark-submit` through its `--py-files` argument by packaging them into a .zip file (see `spark-submit --help` for details). `SimpleApp` is simple enough that we do not need to specify any code dependencies.
    
    We can run this application using the `bin/spark-submit` script:
    > 

  

- server 올리기
    
    ```powershell
    $ $SPARK_HOME/bin/spark-submit --master local[4] 파일 이름
    $ $SPARK_HOME/bin/spark-submit --master local[4] simpleApp.py
    ```
    
    주의 할 점은 서버 올리기 전에 다음 명령어를 통해 SPARK_HOME 경로를 잡아준다.
    
    ```powershell
    $ echo $SPARK_HOME
    ```
    

  

- server 확인
    
     서버 올리고 나서 위쪽으로 살펴보면 다음과 같이 `using xxx.xx.xxx.xxx` 가 있는데 xxx.xx.xxx.xxx:4040 으로 들어가 보면 서버가 정상적으로 올라간 것을 확인 할 수 있다.  
    
    ![](/images/sparkUI/Untitled%203.png)
    
      
    
    만약에 4040 이 먹히지 않으면 다음과 같이 SPARKUI를 찾아 맞는 포트를 찾는다.  
    
    ![](/images/sparkUI/Untitled%204.png)
    
    나는 4040이 잘 작동 되기 때문에 SparkUI에서도 4040으로 찍혀있다.  
    
    서버에 들어가면 다음과 같이 zppName으로 지정한 SimpleApp이 위 오른쪽 상단에 찍혀있는 것을 볼 수 있다.  
    
    ![](/images/sparkUI/Untitled%205.png)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**