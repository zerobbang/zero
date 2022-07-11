---
title: Spring Boot - Setting / Spring Starter Project
date : "2022-07-06"
categories:
- Java
- SpringBoot
tags:
- [SpringBoot]
- [Board]
- [Starter Project]
---

### 진행 과정

- 자바 jdk 설치하기
    - 환경 변수 설정하기
- sts 4 설치 및 환경 설정 하기
- 라이브러리 추가
    - sts4 - web 설치
- 필수 플러그인 설치
    - Mybatis
    - Thymeleaf
- 프로젝트 생성

---

## JAVA JDK 설치 및 설정

Jdk 파일 다운로드하러 가기 → [클릭](https://www.oracle.com/kr/java/technologies/javase/jdk11-archive-downloads.html)

자신의 환경에 맞는 버전으로 jdk 파일을 다운로드를 한 뒤, 기본 설정대로 설치를 진행한다.

### 시스템 환경 변수 설정

- 시스템 환경 변수 편집 > 환경 변수 > **시스템 변수**에 생성 및 변경
    
    ![](/images/springboot_setting/Untitled.png)
    
- JAVA_HOME : jdk 파일이 있는 경로
- Path 편집 > 새로 만들기 > %JAVA_HOME%\lib 추가
    - %JAVA_HOME%\lib를 위로 올려주기 > 우선순위
- CLASSPATH : %JAVA_HOME%\lib 으로 생성 및 변경
    
    ![](/images/springboot_setting/Untitled%201.png)
    
- cmd에서 설치 확인 > Java , Javac 각각 입력 해보기

---

## STS 4 설치 및 기본 세팅

- sts 4 설치 하러 가기 → [클릭](https://spring.io/tools)
- sts 4 세팅 하러 가기 → [블로그](https://zerobbang.github.io/2022/06/14/sts4_install/)

### spring boot 추가 세팅

encodin > Content Types > Text > Spring Properties  File - utf-8설정

![](/images/springboot_setting/Untitled%202.png)

---

## 라이브러리 추가

Help → install new software → sts 검색 → Spring Tool Suite 4 선택 → 마지막에 있는 WEB, XML, JAVA EE …  설치 시작

![](/images/springboot_setting/Untitled%203.png)

---

## 필수 플러그인 추가

### mybatis 설치 하기

- Help → Eclipse Marketplace → mybatis 검색 → **MyBatipse** 설치

### Thymeleaf 설치 하기

- Helo → install new sofhware → http://www.thymeleaf.org/eclipse-plugin-update-site 검색 후 설치
    
    ![](/images/springboot_setting/Untitled%204.png)
    
    ![](/images/springboot_setting/Untitled%205.png)
    

![](/images/springboot_setting/Untitled%206.png)

---

## 프로젝트 생성 - Spring starter project

- new → others → spring starter project 클릭
    
    ![](/images/springboot_setting/Untitled%207.png)
    
    여기서 자바 버전은 jre를 말하는 것이므로 우리가 설치한 jdk가 아니기 때문에 지금은 jdk와 버전이 달라도 상관이 없다.
    
- 다음 의존성들을 추가해준다.
    - Developer Tools
        - Spring Boot DevTools
        - Lombok
        - Spring Configuration Processor
    - SQL
        - Spring Data JPA
        - MyBatis Framework
        - MySQL Driver
    - Template Engines
        - Thymeleaf
    - Web
        - Spring Web

![](/images/springboot_setting/Untitled%208.png)

😀 스프링 부트는 톰캣 서버러를 내장하고 있어서 별도 was설치가 없어도 된다.

  

😥 class 경로 문제 관련해서 에러가 뜨면 → ini 폴더에서 vm의 경로를 jdk bin 폴더로 잡아주기

  

### Spring Starter Projects 설명

![](/images/springboot_setting/Untitled%209.png)

- src/main/java : 자바 파일이 존재하는 곳
- com.board > BoardApplication.java : main( ) 메서드에서는 **SpringApplication.run( )**
을 호출해서 웹 애플리케이션을 실행하는 역할 → 자세한 설명 보러 가기 [클릭](https://bj-lee.tistory.com/2)
- src/main/resources
    - **application.properties** : 웹 애플리케이션을 실행하면서 자동으로 로딩되는 파일. 모든 설정이 들어가 있는 곳
    - static : 정적 자원이 들어가는 폴더 (css, font 등)
    - templates : 스프링 부트는 타임리프 템플릿 엔진의 사용을 권장. JSP와 같이 HTML 내에서 데이터 처리.
- src/test/java : 단위 테스트를 진행 하는 곳
- build.gradle
    - 기존 스프링은 build tool로 pom.xml에 여러 개의 dependency를 추가해서 라이브러리를 관리하는 **메이븐**을 이용. → **라이브러리의 버전 문제, 충돌 문제, 종속적인 문제**
    - **그레이들은 단 한 줄의 코드로 라이브러리를 추가 가능**

---

[[설치 과정 참고한 블로그](https://congsong.tistory.com/12?category=749196)]
  
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**