---
title: Docker 설치
date : "2022-04-12"
categories:
- [Setting]
---


📎 [참고 블로그](https://dschloe.github.io/settings/windows_docker_install/)  

  

- Windows PowerShell → 관리자 권한으로 실행
- wsl2가 설치되어 있어야 한다. [다음을 참고](https://www.lainyzine.com/ko/article/how-to-install-wsl2-and-use-linux-on-windows-10/)

```powershell
wsl --set-default-version 2
```

wsl 버전 2 확인하고 Doker 설치 시작하기  

---

  

### Docker  다운

[여기](https://www.docker.com/products/docker-desktop/)에서 다운 시작  

![](/images/Docker_set/Untitled.png)

자신 환경과 맞는 버전을 다운 받는다. (나는 Windows 진행)  

Docker Desktop Installer.exe 실행하여 설치를 진행한다.  

**Configuration** 창에서 Install required Windows components for WSL 2 와 Add shortcut to desktop 체크하여 설치를 계속 진행한다.  

설치가 완료 되면 재 시작을 진행한다.  

재 시작 후, 재 접속 하면 약관 동의 창이 나타나고 동의 체크 후 Accept 눌러 설치를 완료한다.

   

---

  

### Docker 초기 설정

회원 가입 후 Docker 실행하여 Start 눌러 Tutorial 진행  

Proceed to Docker Desktop 눌러 Docker 실행  

- 오른쪽 상단 ⚙️ 환경 설정

General → Use the WSL 2 based engine  ☑️  → Appply & Restart  

![](/images/Docker_set/Untitled%201.png)

Resource → WSL Integration → Enable Integration with my default WSL distro ☑️ → Apply & Restart  

![](/images/Docker_set/Untitled%202.png)

  

---

  

### Docker 설치 확인

- Windows PowerShell → 관리자 권한으로 실행
- 다음 코드로 Docker 전용 머신 실행 확인

```powershell
$ wsl -l -v
```

![](/images/Docker_set/Untitled%203.png)

- Docker 서버와 클라이언트 정보 확인

```powershell
$ docker version
```

![](/images/Docker_set/Untitled%204.png)

- Docker 실행 중인 컨테이너 확인
    - 실행 중인 컨테이너가 없는 경우
    
    ```powershell
    $ docker ps
    CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
    ```
    
    - 실행 중인 컨테이너가 있는 경우(nginx 실행)
    
    ```powershell
    $ docker ps
    CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                  NAMES
    762037058fc4   nginx:latest   "/docker-entrypoint.…"   3 seconds ago   Up 2 seconds   0.0.0.0:4567->80/tcp   serene_lalande
    ```

  

- Docker 실행 중인 컨테이너 삭제  
    -f 다음은 자신의 CONTAINER ID 입력  

    ```powershell
    $ docker rm -f 762037058fc4
    762037058fc4
    ```

  
  
---

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**