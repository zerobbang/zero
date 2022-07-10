---
title: db 연결 시 주의할 점
date : "2022-07-01"
categories:
- [Etc]
tags:
- [DB]
---

Jsp에서 db연결 후, try,catch문을 통해 사용하여 서버를 실행하다 보면 자꾸 예외가 발생하면서 멈추는 경우가 발생했다. 

```java
finally {
			try {
				if(pstmt!=null) {
					// 예외가 발생할 수 있는 문장 
					pstmt.close();
				}
			} catch (SQLException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
```

그 이유를 찾다보니 db연결을 위해 conn을 생성하고 쿼리 실행을 위해 pstmt를 만들어 실행하고서는 닫아주지 않았다.

 그러면 매번 사용할때마다 pstmt를 계속 새로 실행을 하는데 닫아주지는 않게 되면서 에러가 발생했던 것이다. 그래서 위 코드와 같이 try / catch 문 다음 finally를 통해 방금 사용한 pstmt를 닫아주도록 해주었다.

 모든 pstmt 사용하는 곳에 처리해줘야 한다.
 
---

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**