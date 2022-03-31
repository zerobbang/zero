---
title: Hexo Blog - Hexo Blog 만들기
date : "2022-03-17"
categories:
- [Hexo]
---
## 사전 작업

source/images/Hexo_blog




- 다음 주소 참고
[https://dschloe.github.io/settings/hexo_blog/](https://dschloe.github.io/settings/hexo_blog/)
- hexo를 쓰기 위해 node 설치하기
    
    ![](/images/Hexo_blog/Untitled.png)
    
- LTS 버전 다운받아 관리자 권한으로 설치하면 끝(관리자 권한이 없을 수도 있음)

- 다음 옵션으로 설정해주기
    
    ![](/images/Hexo_blog/Untitled%201.png)
    
    ![](/images/Hexo_blog/Untitled%202.png)
    

## 설치 확인하기

- git bash에서 node 버전 확인
    
    ![](/images/Hexo_blog/Untitled%203.png)
    

## hexo 만들기

- 다음을 입력하여 설치해주기
    
    ```jsx
    npm install -g hexo-cli
    hexo init (사용할 폴더명)
    ```
    
    ![](/images/Hexo_blog/Untitled%204.png)
    
- 위 코드 실행후 자신이 설정할 폴더명으로 바탕화면에 새롭게 폴더가 생긴다.
- 해당 파일을 PyCharm으로 연 후, 터미널에서 git bash로 들어가 다음과 같이 블로그 생성을 한다.
    
    ![](/images/Hexo_blog/Untitled%205.png)
    

- hexo blog가 잘 생성되었는지 hexo server로 확인한다.
    
    ```jsx
    $ hexo server
    ```
    
    위 코드를 치고 기다리면 다음과 같이 로컬 호스트 주소창이 생성되는 것을 확인 할 수 있다.
    
    ![](/images/Hexo_blog/Untitled%206.png)
    
    링크를 클릭해서 들어가면 다음과 같이 기본 블로그 화면이 나온다.
    
    ![](/images/Hexo_blog/Untitled%207.png)
    

### git과 hexo 연결하기

- git에 들어가서 새로운 레포를 만들어준다.
    
    ![](/images/Hexo_blog/Untitled%208.png)
    
- Repository name을 git bash에서 블로그 생성시 설정한 폴더명과 같이 입력해주고 create 버튼을 눌러 생성한다.
 그러면 다음과 같은 화면이 뜨는데 ...or create a new repository on the command line에 있는 코드들을 PyCharm 터미널에 입력해준다.
    
    ![](/images/Hexo_blog/Untitled%209.png)
    
- 중간에 에러가 난다면 git과 연동이 안된 상태이기 때문에 오류에서 알려주는 대로 git id와 username을 입력해준다.

- git push까지 완료가 되고 git을 새로 고침하면 다음과 같이 화면이 바뀐다.
    
    ![](/images/Hexo_blog/Untitled%2010.png)
    

## git에 파일 올리기

- git add ~ or git add .
- git commit -m “입력 메세지”
- git push
    
    ```bash
    git add (파일명)
    # 한꺼번에 다 올리는 경우
    git add .
    
    git commit -m ""
    git push
    ```
    

## 배포 하기

- 블로그 생성 후 처음 배포를 위해 다음과 같이 코드를 입력하여 준다.
    
    ```bash
    npm install
    npm install hexo-server --save
    npm install hexo-deployer-git --save
    ```
    

- _config,yml로 들어가서  url 주소와 마지막에 있는 Deployment를 다음과 같이 변경한다.
    
    ```bash
    url: https://(자신의 유저네임).github.io
    ```
    
    ```bash
    # Deployment
    deploy:
      type: git
      repo: https://github.com/(자신의 유저네임)/(자신의 유저네임).github.io.git
      branch: main
    ```
    

- 다시 git으로 돌아와 새로운 Repository를 만드는데 위 코드 에서 (자신의 유저네임).github.io과 동일하게 파일 명을 설정해주어야 한다.
내 경우에는 다음과 같다. 
`zerobbang.github.io`

- 그 다음 다시 PyCarm의 git bash 창으로 돌아와 다음 코드들을 입력해하여 배포한다.
    
    ```bash
    $ hexo generate
    $ hexo deploy
    ```
    
    완료 후에 깃허브에서 새로고침하면 파일들이 다 올라와있는 것을 확인할 수 있고 주소검색창에 `[zerobbang.github.io](http://zerobbang.github.io)` 입력하여 배포가 된 걸 확인한다.
    

- 다시 쓰고 올릴 때는 위 두 코드를 다시 입력해주면 되는데 더 빠르게 입력하는 방법도 있다.
    
    ```bash
    $ hexo generate -deploy
    $ hexo d -g
    ```
    

- 만약에 git hub에는 잘 올라가는데 hexo 블로그에 적용이 안된다면 다음 코드를 한번 입력하여 캐시를 지워주면 된다. 그래도 안되면 깃 서버 문제일 수 있으니 확인해준다.
    
    ```bash
    $ hexo clean
    ```
---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**