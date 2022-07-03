---
title: JSP에서 Get, Post 방식으로 값 주고 받기
date : "2022-06-29"
categories:
- Java
- Jsp
tag:
- [get]
- [post]
- [Jsp]
---

### 공통 코드

```java
// in A.jsp
<form action ="B.jsp">
	<input name='age' type='text'>
	<button type='submit'>버튼</button>
	<br>
	<input name='num1' type='text'>
	<input name='num2' type='text'>
	<button type="submit">출력</button>
</form>

// in B.jsp
// getParameter는 무조건 String으로 받아옴
	int a = Integer.parseInt(request.getParameter("num1"));
	int b = Integer.parseInt(request.getParameter("num2"));
	int result = a +b;
	
	// A에 전달한다.
	String url = "A.jsp";
```

### get 방식

```java
// in A.jsp
String name = request.getParameter("name");
out.println(name);

// in B.jsp
String appendUrl = "?result="+result;
response.sendRedirect(url+appendUrl);
```

### post 방식

```java
// in A.jsp
String resultFromB = String.valueOf(pageContext.getSession().getAttribute("result"));
out.println(resultFromB);

// in B.jsp
pageContext.getSession().setAttribute("result", result);
response.sendRedirect(url);
```

---

## get방식과 post 방식

### get

- 서버에서 어떤 데이터를 가져와서 보여줄때 사용
- 즉, 받아 온 데이터를 변경하지 않고 사용한다.
- 글의 내용을 보는 경우로 Read or Retrieve일 때 사용
- 클라이언트에서 서버로 어떤 리소스의 정보를 요청하기 위해 사용
- 요청할 때 url 주소 끝에 파라미터로 정보가 포함 → 쿼리 스트링이라고 부른다.
- 데이터를 변경할 수 없기 때문에 안전하다고 본다.

### post

- 데이터를 변경하기 위해 사용한다.
- 글의 내용을 저장 및 수정 하는 경우
- http 메세지의 body에 담아서 전송한다.
- body 타입은 요청 헤더의 content-type요청 데이터 타입에 따라 결정된다.
- body 길이의 제한없이 데이터를 전송할 수 있다.
- 내용이 눈에 들어나지 않는다.
- 개발자 도구 와 같은 툴로 요청 내용 확인 가능하기 떄문에 안전한 방법은 아님.

---
[참고 블로그](https://velog.io/@songyouhyun/Get%EA%B3%BC-Post%EC%9D%98-%EC%B0%A8%EC%9D%B4%EB%A5%BC-%EC%95%84%EC%8B%9C%EB%82%98%EC%9A%94)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**