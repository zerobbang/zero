---
title: SQL 서브 쿼리 정리
date : "2022-04-28"
categories:
- [Sql]
tags: 
- [Sql]
---


SQL 문장 안 보조로 사용되는 또 다른 SELECT 문을 의미한다.  
SELECT or FROM or WHERE 절에 서브 쿼리가 들어 갈 수 있다.  
서브 쿼리 안에 서브 쿼리가 들어 갈 수 있다. (중첩 서브 쿼리)  

### SQL 서브 쿼리 종류

- 메인 쿼리와의 연관성
    - 연관성이 없는 서브 쿼리
    - 연관성이 있는 서브 쿼리

- 형태에 따라
    - 일반 서브 쿼리 (SELECT 절)
    - 인라인 뷰(FROM 절)
    - 중첩 쿼리(WHERE 절)

### 복잡한 서브 쿼리 코드 작성해보기 ( 흐름 파악하기 )

- ERD 란?
    
    다음 그림과 같이 여러 테이블간의 관계를 보여주는 그림이다.  
    이를 토대로 쿼리 작성 시 조인에 이용하기 쉬우며 쿼리 작성 할 때 도움이 된다.  
    그래서 쿼리 작성 하기 전 ERD를 통해 테이블의 흐름을 파악하는 것이 중요하다.
    
    ![](/images/sql_sub/Untitled.png)
    
- DATA 자료의 ERD
    
    ![](/images/sql_sub/Untitled%201.png)
    
    만약 employee 테이블에서 countries 테이블로 가려면 바로 가지 못하고 sales → customers 를 거쳐서 가야 한다.  ( 서로 관계 있는 테이블이 아니기 때문 )  
    

  

**Q.** 연도별 이탈리아의 매출 데이터를 살펴 매출 실적이 가장 많은 사원의 목록과 최대 매출액 추출  

- 사전 정리
    
    table : countries / customers / sales / employees  
    연도 별 사원 별 이탈리아 매출액 구하기
    -- 고객 : customers, countries -> coutry_id  조인
    -- 매출 : 위 결과와 sales 테이블을 cust_id 조인
    -- MAX , GROUP BY 사용
    
    1. 연도별 사원별 매출액 구하기
        
        ```sql
        SELECT
        	SUBSTR (a.sales_month,1,4) AS years   -- 연도만 추출
        	, a.employee_id   -- 직원 id 추출
        	, SUM(a.amount_sold) AS amount_sold  -- 총합 매출액 추출
        FROM sales a, customers b, countries c
        WHERE a.cust_id = b.cust_id
        	**AND b.country_id = c.country_id
          AND c.country_name = 'Italy'
        GROUP BY SUBSTR(a.sales_month,1,4) ,a.employee_id;**
        ```
        
    2. 연도별  최대 최소 매출액 구하기
        
        ```sql
        SELECT 
            years   --  연도 추출
            , MAX(amount_sold) AS max_sold   --  최대 매출액 추출
            , MIN(amount_sold) AS min_sold   --  최소 매출액 추출
        FROM ( 1번 코드 ) K
        GROUP BY years
        ORDER BY years;
        ```
        
    3. 최대 매출액 갱신한 사원 ID, 이름 찾기
        
        ```sql
        SELECT emp.years
        	, emp.employee_id
        	, emp2.emp_name
        	,emp.amount_sold
        FROM (1번코드) emp  --- 연도별 사원별 매출액 테이블
        		, (2번코드) sale  --- 연도별 최대 매출액 테이블
        		, employees emp2  --- 사원 테이블 ( 사원 id , 이름 가져오기 위해 )
        WHERE emp.year = sale.years
        	AND emp.amount_sold = sale.max_sold
        	AND emp.employee_id = emp2.employee_id
        ORDER BY years;
        ```
        
    
![](/images/sql_sub/Untitled%202.png)
    
      
    
---
    
[참고서](http://www.kyobobook.co.kr/product/detailViewKor.laf?mallGb=KOR&ejkGb=KOR&barcode=9788966189984) 오라클 SQL과 PL/SQL을 다루는 기술

**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**