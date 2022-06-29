---
title: JSP로 게시판 만들기 1 - 로그인
date : "2022-06-27"
categories:
- [Java]
tag:
- [Jsp]
- [Mysql]
---

이번 글에서는 JSP를 이용해 Mysql과 DB 연동하여 로그인 페이지를 만들어 보겠다.

### 목차

1. index.jsp
2. login.jsp
3. loginAction.jsp
4. User.java
5. UserDAO.java

---

### index.jsp 파일

 첫 실행은 다음과 같이 자동적으로 default된 값이 있기 때문에 index이름으로 jsp 파일을 생성해준다.

![](/images/jsp_login/Untitled.png)

 그리고 index 파일에서 로그인 링크를 달아주고 로그인 jsp 파일로 넘겨준다.

```jsx
<body>
	<a href="login.jsp">로그인</a>
</body>
```

---

### login.jsp 파일

[다음] bootstrap 파일로 로그인 jsp파일과 css 파일을 불러온다.

### body

body부분에 있는 **form** 에서 우리 환경에 맞게 변경해주어야 한다.

  

- form action에 loginAction.jsp 파일과 연결해준다.
- method 방법은 다른 사람이 관여 하면 안되기 때문에 POST방식

```jsx
<form action ="loginAction.jsp" method="POST">
```

![](/images/jsp_login/Untitled%201.png)

여기서 loginAction.jsp는 login이 돌아가는 환경을 만들어주는 jsp파일로 개인이 생성한 파일 명에 맞춰서 넣어주면 된다.

  

- ✏ 여기서 주의할 점!
    
    form 안의 데이터 들은 submit 되는 순간 name의 이름으로 백엔단으로 값을 넘겨준다. 그래서 다음과 같은 작업을 해줘야 한다.
    

- 그 다음 userID와 userPassword를 logoinAction파일에 넘겨주기 위해 값을 다음과 같이 바꿔준다. ( id와 name과 label을 db에 맞춰 바꿔준다. )

```jsx
<div class="form-floating">
				<input type="email" class="form-control" id="userID" name="userID"
					placeholder="name@example.com"> <label for="userID">Email
					address</label>
			</div>
<div class="form-floating">
				<input type="password" class="form-control" id="userPassword" name="userPassword"
					placeholder="Password"> <label for="userPassword">Password</label>
			</div>
```

---

### loginAction.jsp 파일

여기에서는 사용자가 자신의 ID와 Password를 입력하고 로그인 버튼을 클릭했을 때의 과정을 처리하는 jsp파일이다.

- **class import 하기**

```jsx
<!-- DAO 인스턴스 -->
<%@ page import = "User.UserDAO" %>
<!-- 출력 라이브러리 -->
<%@ page import = "java.io.PrintWriter" %>
<!-- 인코딩 설정 -->
<% request.setCharacterEncoding("UTF-8"); %>
```

- bean 생성
    - 패키지 이름 :  User

```jsx
<jsp:useBean id="User" class="User.User" scope="page"></jsp:useBean>
<jsp:setProperty name="User" property="userID" />
<jsp:setProperty name="User" property="userPassword" />
```

- bean 사용 방법
    
    ```jsx
    <jsp:useBean id="빈이름" class="자바빈클래스명풀패키지로" scope="사용범위"/>
    <jsp:setProperty name="빈이름" property="속성명"  value="설정할값"/>
    <jsp:getProperty name="속성명" property="파라미터명"/>
    ```
    

- **body**

```jsx
<%
		// class UserDAO 객체 생성
		UserDAO userDAO = new UserDAO();
		// login 함수 불러오기
		// jsp파일에서는 User class를 인스턴스화 하지 않았기 때문에
		// 다음과 같이 클래스명.함수로 값을 받아온다.
		int result = userDAO.login(User.getUserID(), User.getUserPassword());
		
		// 1이면 로그인 성공
		// 로그인 실행 결과에 따라 화면에 띄울 스크립트 생성
		if(result==1){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			// 대소문자 조심
			script.println("location.href='index.jsp'");
			script.println("</script>");
		}else if(result ==0 ){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('비밀번호가 잘못되었습니다.')");
			script.println("history.back();");
			script.println("</script>");
		}else if(result==-1){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('아이디가 존재하지 않습니다.')");
			script.println("history.back();");
			script.println("</script>");
		}else if(result == -2){
			PrintWriter script = response.getWriter();
			script.println("<script>");
			script.println("alert('DB에서 오류가 발생했습니다.')");
			script.println("history.back();");
			script.println("</script>");
		}
		%>
```

---

### User.java 파일

User 파일에서는 DB에서 불러온 값들을 변수명으로 지정해준다.

개인 아이디와 비밀번호 같이 db에 있는 값들은 개인 정보 이기 때문에 접근 제한자가 public이 아니라 private으로 다른 사용자가 접근하지 못하도록 생성해야 한다.

- db 컬럼 명 변수 생성
    
    ```jsx
    private String userID;
    private String userPassword;
    private String userName;
    private String userGender;
    ```
    

- toString
    
    ```jsx
    @Override
    	public String toString() {
    		return "User [userID=" + userID + ", userPassword=" + userPassword + ", userName=" + userName + ", userGender="
    				+ userGender + "]";
    	}
    ```
    
- Getter and Setter
    
    ```jsx
      public String getUserID() {
    		return userID;
    	}
    	public void setUserID(String userID) {
    		this.userID = userID;
    	}
    	public String getUserPassword() {
    		return userPassword;
    	}
    	public void setUserPassword(String userPassword) {
    		this.userPassword = userPassword;
    	}
    	public String getUserName() {
    		return userName;
    	}
    	public void setUserName(String userName) {
    		this.userName = userName;
    	}
    	public String getUserGender() {
    		return userGender;
    	}
    	public void setUserGender(String userGender) {
    		this.userGender = userGender;
    	}
    ```
    

source를 통해 getter and setter와 tostring값을 자동으로 불러올 수 있다.

위 함수들을 통해서 불러온 데이터들을 변수에 저장하고 그 변수를 불러올 수 있게 한다.

---

### UserDAO.java 파일

> 🎈 DAO 란?
Data Access Object 의미로 데이터에 접근하는 역할을 맡는 객체를 뜻한다.
> 

- Private 접근 제한자로 db 연결 객체 생성
    
    ```java
    // 자바와 db연결을 위한 객체
    private Connection conn;
    // 쿼리 시작을 위한 준비 객체
    private PreparedStatement pstmt;
    // 쿼리 실행 결과를 담아줄 객체
    private ResultSet rs;
    ```
    

- 생성자 설정 - db연결 준비 ( dbURL, dbID, dbPassword )
    
    ```java
    public UserDAO() {
    		try {
    			String dbURL = "jdbc:mysql://localhost:3306/JSP_TEST?serverTimezone=UTC";
    			// JSP_TEST는 자신이 생성한 db에 맞춰 바꿔줘야 한다.
    			// jdbc : java db connectivity
    
    			String dbID = "root";
    			String dbPassword = "system123";
    			
    			// db 드라이버와 연결 준비
    			// db와 연결하는 드라이버 클래스 찾아 로드
    			Class.forName("com.mysql.jdbc.Driver");
    			// 데이터베이스 드라이버 로드 할 뿐 연결에 관한 행동은 아무것도 안함.
    
    			// 입력받은 dbURL, dbID, dbPassword를 통해 db 연결
    			// 입력받은 파라미터를 갖고 있는 드라이브 서버에 접속할 수 있는 커넥션 객체 가져온다.
    			conn = DriverManager.getConnection(dbURL,dbID,dbPassword);
    			
    		} catch (Exception e) {
    			// TODO: handle exception
    			e.printStackTrace();
    		}
    	}
    ```
    

- 로그인 함수
    
    ```java
    public int login(String userID, String userPassword) {
    		// 유저가 친 해당 아이디 비번 가져옴
    
    		// 실행할 쿼리문 준비
    		String SQL = "SELECT userPassword FROM TABLE_USER WHERE userID=?";
    		// 유저로부터 입력받은 userID와 동일한 값을 갖는 데이터의 suerPassword를 가져온다.
    		
    		try {
    			System.out.println("conn : "+conn);
    
    			// 문자열 쿼리를 pstmt에 대입
    			// 실행할 쿼리문을 prepareStatement로 쿼리 실행 준비
    			pstmt = conn.prepareStatement(SQL);
    			
    			// 첫 번째 물음표에 userId 값 세팅
    			pstmt.setString(1, userID);
    			
    			// 프로그래밍 언어에서 인덱스는 0부터 시작이지만 쿼리에서는 1부터 시작.
    			rs = pstmt.executeQuery(); // 쿼리 실행
    
    			if(rs.next()) {
    				//결과 리스트의 다음 행의 값이 존재하면
    				if(rs.getString(1).equals(userPassword)) {
    					// 남은 것의 첫번째 값이 login 함수로 호출 할 때 전달받은 비번과 같은지 검사
    					return 1; // 로그인 성공
    				}else {
    					return 0; //  실패
    				}
    			}
    			return -1; // 아이디 없음
    		} catch (Exception e) {
    			// TODO: handle exception
    			e.printStackTrace();
    		}
    		return -2; // db 오류
    	}
    ```
    

---

### 서버 Error 잡기

- `com.mysql.jdbc.Driver` error
    
    ![](/images/jsp_login/Untitled%202.png)
    
    드라이버 다운 진행
    
    - 드라이브 다운
        
        [여기](https://dev.mysql.com/downloads/connector/j/) 또는 [여기](https://downloads.mysql.com/archives/c-j/)로 가서 다운 받기 - Platform Independent → zip 다운 진행
        
        ![](/images/jsp_login/Untitled%203.png)
        
    - TomCat 파일 → lib 안에 추가
        
        ![](/images/jsp_login/Untitled%204.png)
        
    - jdk → lib 안에 추가 후, class path 경로 잡아주기
        
        ![](/images/jsp_login/Untitled%205.png)
        

- 500에러 : server 클린 후 재 실행

---

[[참고 블로그]](https://bug41.tistory.com/100)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**