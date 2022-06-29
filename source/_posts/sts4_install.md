---
title: 이클립스 sts4, jdk 설치
date : "2022-06-14"
categories:
- [Setting]
tags:
- [Eclipse]
- [jdk]
---

## 다운로드

  

- [Spring Tools](https://spring.io/tools) 여기로 들어가서 자신의 환경에 맞는 버전으로 다운로드

  

![](/images/sts4_install/Untitled.png)

  

  

- [jdk](https://www.oracle.com/kr/java/technologies/javase/jdk11-archive-downloads.html) 여기로 들어가서 자신의 환경에 맞는 버전으로 다운로드 ( 11과 8 버전을 많이 사용하기 때문에 둘 중에서 고르는 걸 추천. 여기에서는 11 버전으로 진행)
    - 다운 받은 파일을 실행 후, 기본 경로 그대로 다운을 진행하고 설치가 완료되면 다음과 같이 cmd 창에서 버전을 확인한다.

![](/images/sts4_install/Untitled%201.png)

```bash
java -version
javac -version # javac 는 자바 컴파일러를 의미
```

  

### 자바 환경 설정

![](/images/sts4_install/Untitled%202.png)

![](/images/sts4_install/Untitled%203.png)

  

 시스템 속성의 환경 변수로 들어가서 사용자 변수에다가 J`AVA_HOME` 생성 후, 변수 값으로는 위와 같이 `jdk 파일 경로`로 잡아준다.  

  

  

---

  

## 이클립스 sts4

❗위에서 다운 받은 sts4 압축 파일을 풀 때 해당 파일의 이름이 길어서 압축 해제가 되지 못 할 수 있으니 다음처럼 이름을 줄여서 압축 해제 진행한다.  

❗ 압축 해제 할 때 알집으로 진행할 경우 제대로 해제가 안 될 수 있으니 [다음](https://www.7-zip.org/)(7-zip) 이용.

![](/images/sts4_install/Untitled%204.png)

- sts4 압축 해제 하면 다음과 같이 sts4 팡리 안에 있는 contents 압축 파일을 해제한다.

![](/images/sts4_install/Untitled%205.png)

- 원하는 경우 한정 해제한 content 파일을 다른 곳에 복사한 다음 SpringToolSuite4.ini 폴더를 다음과 같이 변경한다. (ram 16GB인 경우 → 최적 환경은 1/8과 1/4이다. )

> - Xms2048m
- Xmx4096m
> 

![](/images/sts4_install/Untitled%206.png)

  

  

---

## sts4 setting

### web developer 설치

Help → Install New Software → web developer 검색 → Java and Web developer tool 설치

![](/images/sts4_install/Untitled%207.png)

### 환경 설정

- Window → Preferences

![](/images/sts4_install/Untitled%208.png)

- encoding → Content Types
    - Java Class File, Text , Text → Java Properties File 의 Default encoding을 utf-8로 변경

![](/images/sts4_install/Untitled%209.png)

![](/images/sts4_install/Untitled%2010.png)

![](/images/sts4_install/Untitled%2011.png)

- encoding → workspace → utf-8 설정

![](/images/sts4_install/Untitled%2012.png)

- encoding → css, html, jsp, xml도 utf-8로 변경

![](/images/sts4_install/Untitled%2013.png)

새로운 워크스페이스 생성하면 위 설정도 같이 다시 바꿔줘야 한다.

🎈여기서 내장된 컴파일러를 사용하지 않고 다른 버전의 컴파일러를 사용하려고 하면 다음과 같은 작업을 진행한다.

- compiler → 11 버전으로 변경 (자신이 실행하고자 하는 파일로 변경)

![](/images/sts4_install/Untitled%2014.png)

- installed → installed JREs
    - Add →  standard VM 클릭 후 next → jre home Directory를 자신이 사용할 jdk가 있는 경로 선택 → Finish  클릭
    - 다음과 같이 해당 jdk 선택 한 후 apply 적용

![](/images/sts4_install/Untitled%2015.png)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**