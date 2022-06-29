---
title: JSP와 JSTL 변수 값 주고 받기
date : "2022-06-28"
categories:
- [Java]
tag:
- [Jstl]
---

### JSTL to JSP

```java
<!-- JSTL to JSP -->
<c:set var="target" value="해피데이"/>
<% String target2 = (String) pageContext.getAttribute("target"); %>
<%= target2 %>
```

JSP에서 JSTL 값을 받아올 때는 getAttribute를 사용해서 가져온다.

### JSP to JSTL

```java
<!-- JSP to JSTL -->
<% String target3 = "비온 뒤 맑음";
	pageContext.setAttribute("target4", target3);%>
<c:out value="${target4}"/>
```

JSTL에서 JSP 값을 받아올 때는 JSP에서 setAttribute한 값을 EL 표현식을 통해서 가져온다.

### 결과

![](/images/jsp_jstl_val/Untitled.png)

---

[[참고 1]](https://2-juhyun-2.tistory.com/140)

[[참고 2]](https://nancording.tistory.com/55) - getAttribute

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**