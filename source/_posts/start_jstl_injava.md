---
title: JSP에서 JSTL 시작하기
date : "2022-06-28"
categories:
- [Java]
tag:
- [Jstl]
---

Java에서 jstl을 사용하려면 사전 세팅이 필요하다.

### JSTL ell 설치

JSTL 의 최신 버전은 [다음](https://tomcat.apache.org/download-taglibs.cgi)에서 다운이 가능하다. ( el 버전 )

(지금 다운 받지 말고 일단 글을 끝까지 읽고 진행하기. 이유가 있음.)

### JSTL 라이브러리 추가

다운 받은 JSTL jar 파일을 해당 자바 프로젝트의 `src/main/webapp/WEB-INF/lib` 안에 복사하여 추가.

그리고 프로젝트 Properties로 들어가서 Java Build Path에서 Class path에 다음과 같이 해당 파일을 추가해준다.

![](/images/start_jstl_injava/Untitled.png)

### JSTL 사용하기 위한 taglib 추가

[[참고]](https://www.tutorialspoint.com/jsp/jsp_standard_tag_library.htm) - taglib

prefix core 사용하기 위해 jsp파일 상단에 taglib 추가

```java
<%@ taglib prefix="C" uri="http://java.sun.com/jsp/jstl/core"%>
```

![](/images/start_jstl_injava/Untitled%201.png)

원래는 taglib 작성하면 위와 같이 에러가 생기지 않는데 지금은 에러가 발생했다.

찾아보니까 현재 JSTL 버전 1.2는 tomcat 버전 7.0.57 이후 최신 버전과 JSP 2.1 이후 버전까지 테스트가 완료되어 사용이 가능 하지만,  JSTL 버전 1.2.3 이후로 나온 버전들은 파싱과 변환에 문제가 있어 사용을 하지 못한다고 한다.

처음에는 나도 위 링크에서 최신 버전을 다운 받아 진행했는데 위와 같은 문제가 발생했다.

### JSTL standard 1.2 버전 설치

![](/images/start_jstl_injava/Untitled%202.png)

[다음](https://mvnrepository.com/artifact/javax.servlet/jstl/1.2)으로 들어가서 JSTL standard 1.2 jar파일 다운을 진행한다.

그리고 위에서 했던 JSTL 세팅을  진행하면 된다.

---

[[에러 참고1]](https://stackoverflow.com/questions/13285826/can-not-find-the-tag-library-descriptor-for-http-java-sun-com-jsp-jstl-core)

[[에러 참고2]](https://downloads.apache.org/tomcat/taglibs/taglibs-standard-1.2.5/README_bin.txt)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**