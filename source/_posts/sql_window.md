---
title: SQL - WINDOW FUNCTION
date : "2022-04-28"
categories:
- [Sql]
tags:
- [Sql]
---


## WINDOW 함수

WINDOW 함수는 분석 함수 또는 순위 함수라고 하며 OVER를 이용해 작성하기 때문에 OVER 함수라고 말하기도 한다.  

기존 RDBMS에서는 컬럼간의 연산, 비교, 연결 또는 집합 조회는 가능하지만 행간의 연산은 복잡하다.  

이는 WINDOW 함수를 사용하면 쉽게 해결할 수 있다.  

- WINDOW 함수 종류

| 구분 | 함수 종류 |
| --- | --- |
| 순위 관련 함수 | RANK, DENSE_RANK, ROW_NUMBER |
| 순서 관련 함수 | FIRST_VALUE, LAST_VALUE, LAG, LEAD |
| 집계 관련 함수 | SUM, MAX, MIN, AVG, COUNT |
| 비율 관련 함수 | CUME_DIST, PERCENT_RANK, NTILE, RATIO_TO_REPORT |
| 통계 관련 함수 | CORR, COVAR_POP, COVAR_SAMP, STDDEV, STDDEV_POP, VARIANCE 등 |

- 기본 코드

```sql
WINDOW 함수 OVER (PARTITION BY col1, col2, ...
						  ORDER BY col3, ...
							WINDOW 절)

```

  

---

참고 사이트 및 실습 코드 

[[블로그]](https://loghada.tistory.com/19)

[[참고서]](http://www.kyobobook.co.kr/product/detailViewKor.laf?mallGb=KOR&ejkGb=KOR&barcode=9788966189984)

[[코드실습]](https://github.com/zerobbang/study_oracle_sql/blob/main/Day4_Ch7.sql)  
  
  
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**