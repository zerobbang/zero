---
title: PL/SQL 기본
date : "2022-05-03"
categories:
- [Sql]
tags:
- [Sql]
---

### PL/SQL

SQL을 확장한 절차적 언어  

프로시저 생성자와 SQL을 통합한 개념  

pl/sql 블록을 실행시키면 서버 프로세서에서 SQL 과 프로시저로 분류하여 실행한다.

### 기본 코드

```sql
-- DBMS_OUTPUT 실행하기 위한 조건
SET SERVEROUTPUT ON
-- 경과 시간 출력
SET TIMING ON
-- 선언부
DECLARE 
	~
-- 실행
BEGIN
	~
	DBMS_OUTPUT.PUT_LINE(~);
-- 예외 처리문
EXCEPTION
	~
-- 블록 종료
END;
-- / : pl/sql 자체 종료 ( bash 스크립트로 실행 시 )
```

 DECLARE에서 변수 선언 할 시 데이터 테이블에서 가져올 값과 데이터 타입이 같아야 한다.  그런데 변수가 많아졌을 때 하나하나 선언 하기 어렵기 때문에 다음과 같이 코딩한다.

```sql
-- 변수명 테이블명.컬럼명%TYPE;
-- 예
DECLARE
	customer_id customers.cust_id%TYPE;
```

### 실습 예제

사원 번호를 입력하면 해당 사원의 급여를 추출해라.

```sql
-- accept ~ prompt 이용해 값을 받아오기
accept emp_num prompt '입력하시오. '

-- 변수 선언
DECLARE
	emp_sal NUMBER(10);
BEGIN 
	-- 데이터 값을 변수에 저장
	SELECT salary INTO emp_sal;
	FROM employee
	WHERE emp_number = &emp_num;

	DBMS_OUTPUT.PUT_LINE('월급은 ' || emp_sal);
END; 
```

### IF문 예제

```sql
BEGIN
	~
	-- 예제 코드
	IF col > 10 THEN
		DBMS_OUTPUT.PUT_LINE('상');
	ELSIF col >7 THEN
		DBMS_OUTPUT.PUT_LINE('중');
	ELSE 
		DBMS_OUTPUT.PUT_LINE('하');
	END IF;
END;
```

### CASE문

```sql
CASE 표현식
	WHEN  ~  THEN
			코드;
	WHEN  ~ THEN
			코드;
	...
	ELSE 
			코드;
END CASE;
```

### 반복문 - LOOP문 사용

**기본 반복문 코드**

```sql
LOOP
	처리문;
	EXIT [WHEN 조건];
END LOOP;
```

**기본 반복문 코드 예**

```sql
-- 구구단
DECLARE
	num NUMBER(10);
BEGIN
	-- 반복문 실행 선언
	LOOP
		num := num + 1;
		DBMS_OUTPUT.PUT_LINE('2 * ' || num || ' = ' || 2 * num);
		EXIST WHEN num = 9;
	END LOOP;
END;
```

LOOP 반복문 실행 → EXIST WHEN 조건에 맞으면 LOOP문 탈출 → END LOOP LOOP문 종료

### WHILE문

조건이 참일 때 다음 LOOP문을 실행한다.

```sql
WHILE 조건
LOOP
	~
END LOOP;
```

### FOR문

```sql
FOR 변수 [REVERSE] 최소..최대
	LOOP
		 반복 실행할 코드
	END LOOP
```

 이중 FOR문이 가능.

### CONTINUE문

조건에 해당하는 경우 LOOP절에서 다음 코드를 실행하지 않고 상단 LOOP조건으로 넘어간다.

```sql
CONTINUE WHEN 조건;
```

### GOTO문

지정한 값으로 제어가 넘어간다.

```sql
<<LABEL1>>
		~
		IF ~ THEN
			GOTO LABEL2
		END IF;
		~

<<LABEL2>>
		~
```

위에서 IF 조건에 해당하면 GOTO 문이 실행이 되고 LABEL1의 코드를 계속 실행하는 것이 아니라 바로 LABEL2 코드로 넘어간다.

## 사용자 함수 생성

### 함수 생성하기

```sql
CREATE OR REPLACE FUNCTION 함수이름 ( num1 NUMBER, ... ) -- 매개변수와 데이터 타입 지정
	RETURN NUMBER; -- 위 매개변수 데이터 타입에 맞춰주면 된다.

IS[AS]
	변수, 상수 등 선언
BEGIN
	코드
	RETURN 반환값;
[EXCEPTION
	예외]
END[함수 이름];
```

### 함수 호출

```sql
-- 숫자 2개를 받는 함수 이름을 fun1이라 했을 경우
SELECT fun1 (num1,num2) reminder -- reminder는 결과값의 컬럼명, 원하는 값으로 변환 가능
FROM DUAL;
```

---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**