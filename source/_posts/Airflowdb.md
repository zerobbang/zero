---
title: Airflow dag 안 돌아가는 문제
date : "2022-04-18"
categories:
- [Setting]
---


만약 안 뜨면 로그아웃 후 에 창 닫고 다시 airflow db reset후에 서버 올리고 airflow scheduler 돌리기  
  
![](/images/Airflowdb/Untitled.png)

화살표 클릭 → trigger dag 클릭하여 실행하기

![](/images/Airflowdb/Untitled%201.png)

![](/images/Airflowdb/Untitled%202.png)

dag파일은 올라왔는데 안되면 scheduler 문제일 수 있다. airflow home 에서 scheduler 관련 메세지가 뜨면 터미널에서 Airflow 경로 다시 확인해보기  

```python
$ echo $AIRFLOW_HOME
```

※ web server, web sechduler 둘 다 echo 경로 잡아주고 시작해야 정상적으로 돌아간다.  

  

- airflow dag 파일 없애려면 다음과 같이 실행해보기
1. `airflow db init`
2. 계정 등록
3. .cfg → load_examples = False 설정
4. `airflow db reset`
5. `airflow webserver` 진행

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**