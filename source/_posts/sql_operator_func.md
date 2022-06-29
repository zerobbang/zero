---
title: SQL 연산자와 기본 함수 정리
date : "2022-04-25"
categories:
- [Sql]
tags:
- [Oracle] 
- [Sql]
---


# 연산자

## 비교 조건식
- ANY
        
    ```sql
    WHERE 컬럼 = ANY (val1, val2, ...)
    ```
        
    괄호 안에 있는 값들 중 하나라도 해당되면 추출한다.  
        
    🖍️ **ANY = SOME**,  OR과 IN 또한 기능은 같지만 형태가 좀 다르다.  
        
    ```sql
    # OR
    WHERE 컬럼 = val1
      OR 컬럼 = val2
      OR ...
        
    # IN
    WHERE 컬럼 IN (val1, val2, ... )
    ```
        
- ALL
        
    ```sql
    WHERE 컬럼 = ALL (val1, val2, ...)
    ```
        
    AND 게이트와 같은 역할이다.  
        
    
      
    
## Like 조건식
    
문자열의 패턴을 검색할 때 사용하는 조건식
    
```sql
WHERE 컬럼 LIKE ' 찾고자 하는 문자열 '
```
    
% ⇒ 몇 글자를 지칭하지 않는다. 한 글자가 올 수 있고 많은 글자가 올 수 있고 아예 없을 수도 있다.  
    
_ ⇒ 한 글자만 지칭한다.  
    
대소문자를 구분하기 때문에 사용할 때 주의한다.  
    
      
    
✔️ 비교해보기
    
A로 시작하는 단어를 찾고 싶다? = A%
    
A로 시작하는 2글자 단어를 찾고 싶다? = A_
    
단어에 A가 들어가는 단어를 찾고 싶다? = %A% 
    

  

# 집합 연산자

## UNION - 합집합 ( 중복 X )

```sql
SELECT ~
FROM ~
WHERE ~

UNION

SELECT ~
FROM ~
WHERE ~;
```

  

  

## UNION ALL - 합집합 ( 중복 O )

```sql
SELECT ~
FROM ~
WHERE ~

UNION ALL

SELECT ~
FROM ~
WHERE ~;
```

  

## INTERSECT - 교집합

```sql
SELECT ~
FROM ~
WHERE ~

INTERSECT

SELECT ~
FROM ~
WHERE ~;
```

  

## MINUS - 차집합

```sql
-- 1번에는 있지만 2번에는 없는 것
SELECT ~
FROM ~
WHERE ~ --1번 

UNION

SELECT ~
FROM ~
WHERE ~;  --2번
```

# 함수

## 숫자 함수

| 함수 | 설명 |
| --- | --- |
| ABS(n) | 절댓값을 반환 |
| CEIL(n) | n과 같거나 가장 큰 정수를 반환 |
| FLOOR(n) | n보다 작거나 같은 정수를 반환 |
| ROUND(n,i) | n을 소수점 자리 i 에서 반올림 |
| TRUNC(n,i) | n을 소수점 자리 i 기준 오른쪽을 버림 |
| POWER(n1,n2) | 제곱근 n1^n2 반환 |
| SQRT( n ) | 루트 값 반환 |
| MOD(n1,n2) | n1/n2의 나머지 값 반환 |
| EXP(n) | 지수 함수 반환 |
| LN(n) | 자연 로그 함수 반환 |
| LOG(n1,n2) | LOG 함수 반환 |

## 문자 함수

| 함수 | 설명 |
| --- | --- |
| CONCAT | ||연산자와 같이 매개 변수로 들어오는 문자를 붙여서 반환 |
| SUBSTR(char,pos,len) | 문자열 char의 pos번째 문자부터 len길이만큼 오른쪽으로 자름 |
| LTRIM ( char, set ) | 문자열 char에서 set문자열부터 왼쪽으로 자름
- set이 문자 중간에 있으면 문자 전체를 반환
- set가 맨 왼쪽에 있어야 함. |
| RTRIM( char, set ) | 문자열 char에서 set문자열부터 오른쪽으로 자름
- set이 문자 중간에 있으면 문자 전체를 반환
- set가 맨 오른쪽에 있어야 함. |
| LPAD(expr1, n, expr2) | expr2를 n자리만큼 왼쪽에 채워 expr1을 반환 |
| RPAD(expr1, n, expr2) | expr2를 n자리만큼 오른쪽에 채워 expr1을 반환 |

## 날짜 함수

| 함수 | 설명 |
| --- | --- |
| ADD_MONTHS ( date, n ) | 날짜 기준으로  달(month)이 n만큼 달 수 연산이 된 날짜를 반환  |
| MONTHS_BETWEEN (date1, date2) | 두 날짜 차이 값을 반환 |
| LAST_DAY ( date) | 해당 월의 마지막 날짜 반환 |
| ROUND ( date, format ) | format 기준으로 날짜를 버림
- ROUND(SYSDATE, ‘month’)
- SYSDATE : 22/04/27
- 결과 : 22/05/01 |
| TRUNC ( date, format ) | format 기준으로 날짜를 버림
- TRUNC(SYSDATE, ‘month’)
- SYSDATE : 22/04/27
- 결과 : 22/04/01 |
| NEXT_DAY ( date, ‘요일’) | 해당 요일에 해당되는 가장 가까운 날짜를 반환 |

## 변환 함수

| 함수 | 설명 |
| --- | --- |
| TO_CHAR | 숫자를 문자열의 형태로 변환 |
| TO_NUMBER | 문자열을 숫자 형태로 변환 |
| TO_DATE | 문자열이나 숫자 형태를 날짜 형태로 변환 |

```sql
-- 예제 코드
SELECT TO_CHAR(SYSDATE,'YYYY-MM-DD') FROM DUAL;
SELECT TO_NUMBER('123456') FROM DUAL;
SELECT TO_DATE('20220427','YYYY-MM-DD HH24LMI:SS')

-- 만약 날짜 변환에서 시간이 출력되지 않는다면 인코딩 문제
-- 변환 해주는 코드
ALTER SESSION SET NLS_DATE_FORMAT = 'YYYY-MM-DD HH24:MI:SS';
```

  

## NULL관련 함수

| 함수 | 설명 |
| --- | --- |
| NVL (expr1, expr2) | expr1이 NULL이면 expr2반환 |
| NVL2(expr1, expr2,expr2) | expr1이 NULL dlaus expr2, 아니면 expr3 |
| COALESCE(expr1, expr2) | expr1이 NULL dlaus expr2, 아니면 expr1 |
| LNNVL (조건식) | 조건식이 FALSE나 UNKNOWN이면 TRUE, TRUE이면 FALSE
= 결과 값을 반대로 출력 |
| NULLIF (expr1, expr2) | expr1 expr2 비교해 같으면 NULL, 아니면 expr1 반환 |

  

# 기본 집계 함수

| 함수 | 설명 |
| --- | --- |
| COUNT | 개수 |
| SUM | 합계 |
| AVG | 평균 |
| MIN / MAX | 최소 / 최대 |
| VARIANCE / STDDEV | 분산 / 표준 편차 |

※ DISTINCT 중복을 허용하지 않는다.

## GROUP BY AND HAVING

- 그룹으로 묶을 때 SELECT 한 값 중 집계 함수를 제외한 값들은 꼭 명시를 해주어야 한다.
- HAVING은 GROUP BY 뒤에 이어 나오며 GROUP BY의 결과 대상으로 다시 필터링 한다.
- ORDER BY와 같은 정렬은 마지막에 위치해야 한다.

```sql
SELECT A, B, SUM(c) C
FROM table_name
WHERE ~
GROUP BY A,B
HAVING SUM(c) > 100000
ORDER BY A;
```

- GROUPING SETS

```sql
SELECT A, B, SUM(c) C
FROM table_name
WHERE ~
GROUP BY GROUPING SETS(A,B);
```

A, B별로 그룹 한 값을 합해서 추출한다.


---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**