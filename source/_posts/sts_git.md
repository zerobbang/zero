---
title: sts4 git 연동하기
date : "2022-06-24"
categories:
- [Setting]
tag:
- [Sts4]
- [git]
---

### 

- 먼저 git에서  해당 주소 복사 해놓기
- sts에서 git repositories로 가기
    
    ![](/images/sts_git/Untitled.png)
    
    ![](/images/sts_git/Untitled%201.png)
    
    ![](/images/sts_git/Untitled%202.png)
    
- git clone 클릭 하면 다음과 같이 자동으로 아까 복사 했던 새로 만든 레포 주소 값이 들어간다.
    
    ![](/images/sts_git/Untitled%203.png)
    
- 여기서 Password에 토큰 값이 들어가야 한다
- 다음을 따라 git 토큰 값을 생성하고 이때 생성된 토큰 값은 다시 확인 할 수 없으니 따로 파일에 저장해놓는다.
- Developer Settings → Personal access tokens → Generate new token
    
    ![](/images/sts_git/Untitled%204.png)
    
- 새 토큰 생성할 때 어디 까지 권한을 줄지 체크 박스가 나타나는데 어디서 사용될지 모르니 다 체크! (선택)  
- 그렇게 토큰 값을 받아오고 sts에 집어넣고 완료를 하면 다음과 창이 뜨는데 No를 누르고 넘어간다.  
    
    ![](/images/sts_git/Untitled%205.png)
    
- 추가할 프로젝트를 다음과 같이 진행하면 된다.  

---

### git에 프로젝트 올리기

- git에 올릴 자바 프로젝트 우클릭 → Team  
    
    ![](/images/sts_git/Untitled%206.png)
    
- 체크 박스에 체크가 되어있으면 풀어주고 Repository에 연결할 레포를 선택하고 Project 리스트에서 해당 프로젝트를 클릭하고 완료한다.  
    
    ![](/images/sts_git/Untitled%207.png)
    
- 정상적으로 연결이 완료 되면 다음과 같이 프로젝트 옆에 연동된 깃 레포 이름이 나타난다.  
    
    ![](/images/sts_git/Untitled%208.png)
    
- 커밋하기
    
    ![](/images/sts_git/Untitled%209.png)
    
    ![](/images/sts_git/Untitled%2010.png)
    
- 스테이지에 올릴 파일을 선택하여 올린 후 커밋 메세지를 작성하고 커밋을 진행한다.
    
    ![](/images/sts_git/Untitled%2011.png)
    
    ![](/images/sts_git/Untitled%2012.png)
    
    ![](/images/sts_git/Untitled%2013.png)
    
    ![](/images/sts_git/Untitled%2014.png)


---

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**