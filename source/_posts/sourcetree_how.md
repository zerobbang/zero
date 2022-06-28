---
title: 소스 트리 사용법 및 충돌 해결
date : "2022-06-24"
categories:
- [Setting]
- [Error]
tag:
- [sourcetree]
- [error]
- [merge]
---

## 새로운 repository 만들기

- git에서 새로운 레포를 만들고 레포의 주소를 복사해와서 소스 토리에 새 레포 생성한다.
    
    ![](/images/sourcetree_how/Untitled.png)
    

## Reset과 Revert

### **Reset**

![](/images/sourcetree_how/Untitled%201.png)

- 완전 **초기화** 시킨다.
- 미래( 내가 돌아갈 시점 이후의 푸쉬 )의 내역을 지우면서 되돌아간다.
- 돌아갈 커밋 시점에서 우클릭 후 → Reset current brach to this commit. ( 이 커밋까지 현재 브런치 초기화 )
- 이 커밋까지 현재 브런치 초기화를 진행하면 돌아간 시점의 **커밋 이전**으로 돌아간다.
- 삭제된 커밋들은 staging area로 돌아간다.

![](/images/sourcetree_how/Untitled.jpeg)

- index - 스테이지에 올라간 상태 / working tree - 스테이지에 올라가지 않은 상태
    
    ![](/images/sourcetree_how/Untitled%202.png)
    
- 종류
    - soft
        - index에 올라온 수정사항 보존, working tree에 올라온 수정사항 보존
        - Head 위치 변경 O
    - mixed
        - index에 올라온 수정사항 취소, working tree에 올라온 수정사항 보존
        - Head 위치 변경 O
    - hard
        - index에 올라온 수정사항 취소, working tree에 올라온 수정사항 보존
        - Head 위치 변경 O
        - staging area까지 모두 삭제 → 지양

### Revert

![](/images/sourcetree_how/Untitled%203.png)

![](/images/sourcetree_how/Untitled%204.png)

- Reset과 달리 내가 돌아가는 내역까지 기록되면서 돌아간다.
- 내가 돌아갈 시점의 커밋 말고 그 다음 커밋인 잘못한 커밋 버전에서 진행한다.
- 잘못한 커밋에서 우클릭 후 → Reverse commit

### 정리

reset : 청소 → 역사도 없어지고 선택 상태로 변경

reverse : 청소 x  ( 백업 기능 )→ 역사는 남아있지만 선택 상태로 변경 

## Checkout

- 브랜치 이동 또는 예전 커밋으로 돌아가는 것을 의미.
- 원하는 커밋을 더블 클릭 → 해당 버전으로 돌아간다.
- Checkout 후 파일 수정 → Head(임시) 브랜치 생성. 다른 브랜치 이동하면 사라짐.
- 사라지지 않기를 원하면 새로운 브랜치 생성하여 병합.

![](/images/sourcetree_how/Untitled%205.png)

---

## 소스트리와 깃을 사용해서 협업 환경 만들기 및 충돌 해결

### collaborators 추가

- setting > collaborators ( git )
    
    ![](/images/sourcetree_how/Untitled%206.png)
    
    사람을 초대하거나 메일을 통해 초대에 응답하면 공동 관리자로 등록 된다.
    

### 병합 충돌 해결

git을 통해서 협업을 하다보면 충돌이 발생하는 일이 발생하는데 다음과 같은 방법으로 충돌 해결이 가능하다.

우선, 병합 충돌이 일어난 경우에는 같은 트리의 파일을 다른 사용자가 파일을 변경하여 push하였는데 내가 그 사실을 모르고 pull 없이 push를 하게 되면 병합 충돌이 생긴다.

- push → 병합 충돌로 push 불가 error 발생
    
    ![](/images/sourcetree_how/Untitled%207.png)
    
- pull → pull로 당긴 후 push하려고 해도 pull 자체가 충돌을 해결해야 정상 작동.
    
    ![](/images/sourcetree_how/Untitled%208.png)
    
- 파일 상태로 가서 우클릭 → 충돌 해결 → 외부 / 내것 / 저장소 중에서 택 1

![](/images/sourcetree_how/Untitled%209.png)

- 둘다 가져와서 할거면 외부 병할 툴 시작하고 꺽새 안의 내용을 수정해주면 된다.
- 내것이나 저장소로 해결하면 다음과 같은 알림창에서 예를 클릭한 후 커밋 해주면 된다.
    
    ![](/images/sourcetree_how/Untitled%2010.png)
    

---

### 사용 팁 - 임시 저장하기

- 지금까지 내용을 커밋하지 않고 임시 저장을 하고 다른 작업을 해야할 경우
- 브랜치를 새로 하나 생성한다 . ( main2 )
    
    ![](/images/sourcetree_how/Untitled%2011.png)
    
- 원래 main 브랜치에서 임시 커밋 진행
- main2 ( 새로 만든 브랜치 )로 체크 아웃 진행
    
    ![](/images/sourcetree_how/Untitled%2012.png)
    
- 그대로 다른 작업을 수행하다가 임시 커밋한 내용으로 다시 돌아가게 된 경우, 다시 main으로 돌아가 임시 저장한 파일을 마무리하고 저장.
- 그러면 다음과 같은 상태가 되고 여기서 커밋 진행 할 때 **덮어쓰기**로 진행
    
    ![](/images/sourcetree_how/Untitled%2013.png)
    
- 그리고 커밋 내용 번경 후, 다음과 같은 창이 뜨면 예 누르고 완료하면 된다.
    
    ![](/images/sourcetree_how/Untitled%2014.png)
    
    ![](/images/sourcetree_how/Untitled%2015.png)
    

### 정리

1. main1 임시 커밋
2. main2로 checkout
3. 다시 main1로 이동 후, 작업 마무리
4. 커밋 → 덮어쓰기 amend
5. 필요의 경우 강제 추시 force 진행
- 임시 생성한 브랜치에서는 임시 커밋 전 내용이 저장되어 있고, 임시 커밋을 덮어쓰기해도 임시 브랜치에서는 이전 작업과 동일한 상태
- 해보고 싶은 방법이 있으면 따로 브랜치를 생성하여 작업하면 코드가 섞이는 것을 방지할 수 있다.
- 잘못된 방법의 코딩이어서 되돌아가라면 해당 가지를 삭제하면 된다.

---

[[참고 블로그]](https://webstudynote.tistory.com/28)

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**