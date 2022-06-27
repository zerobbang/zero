---
title: git 로그인 정보 삭제 및 변경
date : "2022-06-26"
categories:
- [Setting]
tag:
- [Git]
---


기존 컴퓨터에 다른 git 유저의 로그인 정보가 담겨있거나 다른 어떠한 이유로 로컬에 저장된 git 유저의 정보를 바꿔야 할 때가 있다.  

그럴때는 다음 방법들을 따라서 해보면 된다.

- 현재 로그인 된 유저의 정보를 자신의 것인지 확인한다.

```java
git config user.name
git config user.email
git config --list
```

- 만약, 확인한 정보가 내 정보가 아닐 경우 다음 코드를 이용해서 변경이 가능하다.

```java
git config --global user.name
git config --global user.email
```

 그리고 다시 첫 번째 코드들을 이용해서 변경이 잘 이루어졌는지 확인한다.

- 위 과정으로 변경 완료했다고 하여 기존 git 정보가 다 바뀐것이 아니다.
- 제어판 → 사용자 계정 → 자격 증명 관리자를 통해 git 정보를 삭제한다.
- windows 자격 증명에서 기존의 git 계정을 삭제 진행한다.

---

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**