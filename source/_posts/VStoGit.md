---
title: VSCode git 연동 하기
date : "2022-04-20"
categories:
- [Setting]
---


VSCode에서 공부한 내용을 git에 올려보자! 😛  

[참고](https://earth-95.tistory.com/87)

  

- Git hub에서 새로운 Repo 생성하기

![](/images/VStoGit/Untitled.png)

repo 이름을 설정하고 Add a Readme file 클릭하여 새로운 repo 생성한다.  

※이때 생성된 repo는 **main** 임을 기억하자.  

  

- VSCode에서 git과 연동할 폴더를 연 후에 Source control 탭을 클릭한다.
    
    ![](/images/VStoGit/Untitled%201.png)
    
- git과 연동되지 않은 폴더일 경우 다음과 같은 화면이 나타나고 여기서 Initialize Repository 클릭
    
    ![](/images/VStoGit/Untitled%202.png)
    
- Changes 폴더에서 git에 올릴 파일을 선택하여 클릭한다.
    
    ![](/images/VStoGit/Untitled%203.png)
    
    ![](/images/VStoGit/Untitled%204.png)
    
- 변경 사항들에 대해 commit 하기 위해 상단의 체크를 클릭하고 메모 입력 후에 Enter를 친다.

  

지금까지 과정은 로컬 저장소에서 commit한 것이기 때문에 git에서는 아직 확인 할 수 없다.  

git에서 확인하기 위해 업로드를 진행한다.  

  

---

- VSCode에서 터미널 창 열기 (처음 연결할 때만 작성)
    
    ```python
    git remote add origin 주소
    ```
    
    ![](/images/VStoGit/Untitled%205.png)
    
     주소는 git에 올릴 repo 주소를 복사해온다.
    
    ![](/images/VStoGit/Untitled%206.png)
    
- 원격 저장소에 있는 파일들을 로컬 저장소로 가져온다.
    
    ```python
    git pull origin main --allow-unrelated-histories
    ```
    
    bash 창은 master이지만 git repo가 main이기 때문에 main으로 가져온다.  
    
- 다시 로컬 저장소에 가져온 파일들을 원격 저장소에 반영
    
    ```python
    git push -u origin master
    ```
    
- 처음 연동 할때는 git hub 허용 관련 창이 뜨니 허용하면서 따라 나오는 안내에 따라 git과 연동을 한다.
- 이제 git으로 돌아가면 다음과 같은 화면을 뜨고 Compare & pull request 클릭한다.
    
    ![](/images/VStoGit/Untitled%207.png)
    
- 그 다음 메세지를 입력하고(선택) create pull request 클릭한다.
    
    ![](/images/VStoGit/Untitled%208.png)
    
- Merge pull request → Confirm merge 하면 연동 끝!
    
    ![](/images/VStoGit/Untitled%209.png)
    
    ![](/images/VStoGit/Untitled%2010.png)
    
    ![](/images/VStoGit/Untitled%2011.png)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**