---
title: Vscode가 git main에 올라가지 않을 때
date : "2022-04-21"
categories:
- [Setting]
---


이유를 모르겠지만 동일한 방법으로 git에 vscode를 올렸는데 master에는 올라가지만 main 에는 올라가지 않는 문제가 생겼다.  

해결하려다 꼬여서 새로운 파일을 만들고 테스트로 하나 올려보니 잘 작동해서 문제가 해결되었다고 생각했다.  

아니 근데 나머지 파일들을 올리는데 main에 올라가지 않는 문제가 또..  

![](/images/vstogitError/Untitled.png)

위처럼 안내 창이 나와야 하는데 안 나온다...  

그래서 문제가 있다고 생각했는데 살펴보니 직접 올리는 법이 있다.  

해당 repo의 Pull requests 에 들어가서 직접 올릴 수 있다.  

![](/images/vstogitError/Untitled%201.png)

저기서 Neww pull request 클릭하면  master에는 올라가고 main에는 미처 올라가지 못한 파일들이 있다.  

거기서 안내에 따라 하나 하나 올려주면 끝!

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**