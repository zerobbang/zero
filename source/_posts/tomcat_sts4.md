---
title: JSP, TomCat sts4에서 시작하기 - JSP로 로그인 페이지 만들기 1
date : "2022-06-27"
categories:
- [Setting]
- [Jsp]
tag:
- [Jsp]
- [Tomcat]
---

### TomCat 설치

[여기](https://tomcat.apache.org/download-90.cgi)에서 자신의 환경에 맞는 버전으로 다운로드 하기 - version 9 download

  

---

### Dynamic web project 생성하기

- new - dynamic web project or others → 검색
    
    ![](/images/tomcat_sts4/Untitled.png)
    

- 만약에 Dynamic web project가 보이지 않는다면….?!?!  
    
    **방법 1.** MarketPlace → Eclipse web developer tools 3.25 설치 한다.  
    
    **방법 2.** MarketPlace → sts3 add on for spring tools 4 설치 한다.
    
    다운로드 하다가 다음 경고 창이 발생하면 그냥 ok 누르고 **밑에 새로** 뜬 창을 열어 설치를 계속 진행하면 된다.
    
    ![](/images/tomcat_sts4/Untitled%201.png)
    
    **방법 3.** help → new install software → 다음 밑에서 두번째를 설치 진행한다 .(Spring Tool Suite 4 ~ download ~ /sts4/update/latest)
    
    ![](/images/tomcat_sts4/Untitled%202.png)
    

- Context root에 프로젝트 이름을 설정해 준 후 다음 창이 나타나면 ok누르고 생성한다.
    
    ![](/images/tomcat_sts4/Untitled%203.png)
    
    ![](/images/tomcat_sts4/Untitled%204.png)
    
- 정상적으로 설치가 완료되면 explorer에서 다음과 같은 상태를 확인할 수 있다.
    
    ![](/images/tomcat_sts4/Untitled%205.png)
    

---

### Emmet 설치하기

다음은 자동완성을 지원해주는 툴로 선택 사항으로 설치를 진행한다.

[[참고1]](https://ucong-9796.tistory.com/315) , [[참고2]](https://dlagusgh1.tistory.com/391)

만약 tab키가 안 먹을 경우 window - preference - Emmet 검색 후 확장자에 .jsp 추가해 줬는지 확인 해 준다.

- 예외 ) 만약 jsp 생성 파일 앞에서 자꾸 빨간 에러줄 버그가 생기면….?!?!
    
    **방법 1.** 프로젝트 - properties - project facets - java - 오른쪽에 있는 run time 탭 - 아파치 톰 캣 버전 9 선택 ( 자신이 설치한 버전 )
    
    ![](/images/tomcat_sts4/Untitled%206.png)
    
    **방법 2.** 해당 프로젝트의 Properties 로 들어가기
    
    Java Build Path → Classpath → Add libaray…
    
    ![](/images/tomcat_sts4/Untitled%207.png)
    
    ![](/images/tomcat_sts4/Untitled%208.png)
    
    ![](/images/tomcat_sts4/Untitled%209.png)
    
    ![](/images/tomcat_sts4/Untitled%2010.png)
    

---

### Server 실행하기

- server가 없으면 server - new server 통해 서버 불러오기
    
    ![](/images/tomcat_sts4/Untitled%2011.png)
    
    ![](/images/tomcat_sts4/Untitled%2012.png)
    
- Server 실행하기
    - 우리는 따로 다운 받은 서버 ( TomCat ) 이 있기 때문에 Choose an existing server를 선택하여 진행
        
        ![](/images/tomcat_sts4/Untitled%2013.png)
        
        ![](/images/tomcat_sts4/Untitled%2014.png)

---

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**