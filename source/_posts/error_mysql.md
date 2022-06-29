---
title: MySQL - Error Code - 1046. No database
date : "2022-06-28"
categories:
- [Error]
tag:
- [MySQL]
---

전날 까지MySQL을 잘 사용하다가  다시 사용하기 위해 열고 실행 시켰더니 다음과 같은 에러가 발생하며 정상 작동이 되지 않았다.

```scheme
**Error Code: 1046. No database selected Select the default DB to be used by double-clicking its name in the SCHEMAS list in the sidebar.**
```

 이를 해결하는 방법은 매우 간단하다.

default DB를 지정해주지 않으면 매번 실행할 schema를 입력해주어야 하는데 다음과 간단한 세팅으로 해결 가능하다.

사용할 DB를 우클릭하면 Set as default Schema 라는 게 보일 텐데 그걸 클릭해주면 끝!

---

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**