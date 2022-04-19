---
title: Install VScode (wsl)
date : "2022-04-19"
categories:
- [Setting]
---


📎 [참고 블로그](https://dschloe.github.io/settings/vscode_wsl2/)  

  

- [vs code 설치](https://code.visualstudio.com/download) (**System Installer**로 설치)
- 설치 시 환경 변수 체크 확인
    
![](/images/VScodeWSL/Untitled.png)
    
- 설치 완료 후 **재부팅** 필요.

---

### Remote WSL 연동

- Extention 버튼 클릭 →  Remote WSL 검색 후 설치
    
![](/images/VScodeWSL/Untitled%201.png)
  
- 설지 완료 전 다음 사항들을 모두 체크 후 Mark Done 클릭
    
![](/images/VScodeWSL/Untitled%202.png)

- Open Foler → airflow_test 폴더 오픈 ( WSL에서 설치했던 파일 )
- Menu → Terminal → WSL 선택
    
![](/images/VScodeWSL/Untitled%203.png)
    
- 서버 돌려보기 (airflow)
    
    ```powershell
    # 가상 환경 설정
    source venv/bin/activate
    # 서버 실행
    airflow webserver -p 8081
    ```
    
![](/images/VScodeWSL/Untitled%204.png)

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**