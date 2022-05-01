---
title: SQL JOIN 정리
date : "2022-04-28"
categories:
- [Sql]
tags: 
- [Sql]
---


JOIN에 대해 간단히 설명하면 다음과 같다.  

보통 메인 쿼리를 a, 서브 쿼리를 b로 명칭 한다.  

조인 연산자에 따른 구분 : 동등 조인, 안티 조인  

조인 대상에 따른 구분 : 셀프 조인  

조인 조건에 따른 구분 : 내부 조인, 외부 조인, 세미 조인, 카타시안 조인  

기타 : ANSI 조인  

  
조인의 관계를 그림으로 간단하게 표현하면 다음과 같다.  

![](/images/sql_join/join-outer.png)

## 내부 조인

### 동등 조인

‘ = ‘를 사용하여 조인을 진행한다.  

```sql
WHERE a.column_name = b.column_name
```

### 세미 조인

서브 쿼리를 사용하여 서브 쿼리에만 존재하는 데이터를 메인 쿼리에서 추출한다.  

중복 허용 X  ( 일반 조인의 경우 중복 값도 같이 추출된다.)  

- exists 사용
    
    ```sql
    SELECT col_name1, col_name2
    FROM table_name1 a
    WHERE EXISTS(SELECT * FROM table_name2 b
                    WHERE a.col_name1 = b.col_name1
                    AND b.col_name3 > 3000)
    ORDER BY a.col_name2;
    ```
    
- in 사용
    
    ```sql
    SELECT col_name1, col_name2
    FROM table_name1 a
    WHERE a.col_name1 IN (SELECT b.col_name1 FROM table_name2 b
                                WHERE b.col_namae3> 3000)
    ORDER BY col_name2;
    ```
    

### 안티 조인

sub query에 없는 main query 의 데이터만 추출한다.  

조인 조건이 서브 쿼리 밖에 → NOT IN  

조인 조건이 서브 쿼리 안에 → NOT EXISTS  

- NOT IN
    
    ```sql
    SELECT a.employee_id, a.emp_name, a.department_id, b.department_name
    FROM employees a, departments b
    WHERE a.department_id = b.department_id 
        AND a.department_id NOT IN(SELECT department_id FROM departments 
                                        WHERE manager_id IS NULL);
    ```
    
- NOT EXISTS
    
    ```sql
    SELECT count(*)
    FROM employees a
    WHERE NOT EXISTS (SELECT 1 FROM departments b
        WHERE a.department_id = b.department_id 
        AND manager_id is NULL);
    ```
    

### 셀프 조인

자기 자신을 조인  

```sql
SELECT a.employee_id, a.emp_name, b.employee_id, b.emp_name, a.department_id
FROM employees a, employees b
WHERE a.employee_id < b.employee_id   --1.
    AND a.department_id = b.department_id
    AND a.department_id = 20;
```

  

# 외부 조인

일반 조인을 확장한 개념  
데이터가 NULL이거나 해당 행이 아예 없더라도 데이터를 모두 추출.  
외부 조인은 조인 조건에 해당하는 곳에 모두 +를 붙여줘야 한다.  

```sql
SELECT a.employee_id, a.emp_name, b.job_id, b.department_id
FROM employees a, job_history b
WHERE a.employee_id = b.employee_id(+)
    AND a.department_id = b.department_id(+);
```

- 외부 조인 시 참고 해야 할 사항
    
    1. 조인 대상 테이블 중 데이터가 없는 테이블 조인 조건에 (+)를 붙인다.
    2. 외부 조인의 조인 조건이 여러 개일 떄 모든 조건에 (+)를 붙인다.
    3. 한 번에 한 테이블에만 외부 조인을 할 수 있다.
    4. (+) 연산자가 붙은 조건과 OR를 같이 사용할 수 없다.
    5. (+) 연산자가 붙은 조건에는 IN 연산자를 같이 사용할 수 없다. (단, IN절에 포함되는 값이 1개일 때는 사용 가능)
    

## 카타시안 조인

WHERE 절에 조인 조건이 없는 조인을 의미한다.  
FROM 절에는 명시했지만 조인 조건이 없다.  

```sql
SELECT a.employee_id, a.emp_name, b.department_id, b.department_name
FROM employees a, departments b;
```

## ANSI 조인

ANSI SQL 문법을 사용한 조인을 의미한다.  
조인 조건이 WHERE 절에 존재하는 것이 아니라 FROM 절에 들어간다.  
내부 조인과 외부 조인이 존재  
JOIN이 명시 되고 조인 조건은 ON 으로 명시한다.  
ON 대신 USING사용 가능한데 그때는 컬럼명만 명시한다.  

### 내부 조인

```sql
# 기본
SELECT a.employee_id, a.emp_name, b.department_id, b.department_name
FROM employees a, departments b
WHERE a.department_id = b.department_id
    AND a.hire_date >= TO_DATE('2003-01-01','YYYY-MM-DD');

# ANSI 문법
SELECT a.employee_id, a.emp_name, b.department_id, b.department_name
FROM employees a
INNER JOIN departments b
    ON (a.department_id = b.department_id)
WHERE  a.hire_date >= TO_DATE('2003-01-01','YYYY-MM-DD');

# USING 사용
SELECT a.employee_id, a.emp_name, department_id, b.department_name
FROM employees a
INNER JOIN departments b
    USING (department_id)
WHERE  a.hire_date >= TO_DATE('2003-01-01','YYYY-MM-DD');
```

### 외부 조인

```sql
-- 기본 문법
SELECT a.employee_id, a.emp_name, b.job_id, b.department_id
FROM employees a, job_history b
WHERE a.employee_id = b.employee_id(+)
AND a.department_id = b.department_id(+);
-- ANSI 문법 - left join
SELECT a.employee_id, a.emp_name, b.job_id, b.department_id
FROM employees a
LEFT OUTER JOIN job_history b
 ON (a.employee_id = b.employee_id
    AND a.department_id = b.department_id);
-- ANSI 문법 - right join
SELECT a.employee_id, a.emp_name, b.job_id, b.department_id
FROM job_history b
RIGHT OUTER JOIN employees a
 ON (a.employee_id = b.employee_id
    AND a.department_id = b.department_id);
-- OUTER 생략 가능
SELECT a.employee_id, a.emp_name, b.job_id, b.department_id
FROM employees a
LEFT JOIN job_history b
 ON (a.employee_id = b.employee_id
 AND a.department_id = b.department_id );
```

## CROSS 조인

ANSI 조인의 카타시안 조인이다.  

```sql
-- CROSS 조인
SELECT a.employee_id, a.emp_name, b.department_id, b.department_name
FROM employees a
CROSS JOIN departments b;
```

## FULL OUTER 조인

외부 조인 중 하나로 ANIS 조인에서만 가능.  
기존 외부 조인은 한 쪽에만 NULL이거나 없는 데이터를 추출했다면 이번에는 양 쪽에서 NULL이거나 없는 데이터를 모두 추출한다.

```sql
SELECT a.emp_id, b.emp_id
FROM hong_a a
FULL OUTER JOIN hong_b b
    ON (a.emp_id = b.emp_id);
```

- 각 각 테이블 자료 형태
    
    
    | A table | B table |
    | --- | --- |
    | 10  | 10 |
    | 20 | 20 |
    | 40 | 30 |
- FULL OUTER 조인 결과
    
    ![](/images/sql_join/Untitled.png)
    

---

[참고서](http://www.kyobobook.co.kr/product/detailViewKor.laf?mallGb=KOR&ejkGb=KOR&barcode=9788966189984) 오라클 SQL과 PL/SQL을 다루는 기술  
  
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**