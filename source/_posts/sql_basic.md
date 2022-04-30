---
title: SQL 기본 (Table , View 생성 및 조회 , SELECT/INSERT/UPDATE문 )
date : "2022-04-25"
categories:
- [Sql]
tags:
- [Oracle] 
- [Sql]
---


### Table 생성

```sql
CREATE TABLE [스키마.]t_name (
			col1  data_type1
			, col2 data_type2
			, ...
) [TABLESPACE 테이블 스페이스 명];
```

[ ] 생략 가능 한 내용이며, 스키마 생략하면 현재  로그인한 스키마 이름으로 생성된다.  그리고 TABLESPACE는 해당 사용자의 DEFAULT값으로 생성된다.  

- 제약 조건 설정하기

```sql
constraints check변수명 check ( 컬럼명 in ('a','b'))
CONSTRAINT CK_변수명 CHECK ( 변수명 in ('a','b'))
CONSTRAINT PK_테이블명 PRIMARY KEY (변수명)
```

   

### Table 변경

```sql
ALTER TABLE [스키마.]테이블명 ~ (목적에 따라 변경)
```

- 컬럼명 변경

  ```sql
  RENAME COLUMN 변경 전 컬럼명 TO 변경 후 컬럼명;
  ```

- 컬럼 데이터 타입 변경

  ```sql
  MODIFY 컬럼명 데이터 타입;
  ```

- 컬럼 추가

  ```sql
  ADD 컬럼명 데이터 타입;
  ```

- 컬럼 삭제

  ```sql
  DROP COLUMN 컬럼명;
  ```

- 제약 조건 추가 - 기본키 추가

  ```sql
  ADD CONSTRAINTS 제약조건명 PRIMARY KEY (컬럼명, ...);
  ```

- 제약 조건 삭제

  ```sql
  DROP CONSTRAINTS 제약조건명;
  ```

  

### Table 복사

```sql
CREATE TABLE [스키마.]새로운 테이블명 AS
SELECT 컬럼1, 컬럼2, ... ( OR * )
FROM 복사 대상 테이블명;
```

  

### Table 삭제

```sql
DROP TABLE [스카마.]테이블명 [CASCADE CONSTRAINTS]
```

`CASCADE CONSTRAINTS` :  해당 테이블의 제약 조건도 함께 자동 삭제  

  

## View

### View 생성

```sql
CREATE OR REPLACE VIEW [스키마.]뷰명 AS SELECT 문장;
```

문장 → SELECT ~ FROM ~ WHERE 의 형태

  

### View 삭제

```sql
DROP VIEW [스키마.]뷰명;
```

  

  

## Index

### Index 생성

```sql
CREATE [UNIQUE] INDEX [스키마.]인덱스명 ON [스키마.]테이블명(컬럼1, ...);
```

### Index 삭제

```sql
DROP INDEX [스키마.]인덱스명;
```

  

  

## 제약 조건 조회

```sql
SELECT constraint_name, constraint_type, table_name, search_condition
FROM user_constraints
WHERE table_name = '테이블명'
```

```sql
SELECT index_name, index_type, table_name, uniqueness
FROM user_indexes
WHERE table_name = '테이블명';
```

## Error 메세지

```sql
오류 보고 -
SQL 오류: ORA-00932: 일관성 없는 데이터 유형: DATE이(가) 필요하지만 NUMBER임
```

→ 데이터 타입이 다름.  

  

```sql
오류 보고 -
SQL 오류: ORA-00947: 값의 수가 충분하지 않습니다
```

→ 컬럼 수와 입력 값 개수가 다름.  

  

```sql
오류 보고 - 
ORA - 00001: 무결성 제약 조건 (ORA USER.SYS C007452)에 위배됩니다
```

→  중복 값 허용되지 않는다.  

  

```sql
오류 보고 -
ORA-01400: NULL을 ("ORA_USER"."EX2_8"."COL1") 안에 삽입할 수 없습니다
```

→ PRIMARY KEY는 NULL값 가질 수 없다.  

  

```sql
오류 보고 -
ORA-00001: 무결성 제약 조건(ORA_USER.SYS_C007455)에 위배됩니다
```

→ 같은 데이터 값을 PRIMARY KEY 에 입력 불가 한다. (중복 허용 X)  

  

```sql
오류 보고 -
ORA-02290: 체크 제약조건(ORA_USER.CHECK2)이 위배되었습니다
```

→ CHECK 조약 조건에 위배된다.  

  

  

## SELECT

- SELECT문의 기본 틀
    
    ```sql
    SELECT * 또는 컬럼
    FROM 테이블 또는 뷰
    WHERE 조건
    ORDER BY 컬럼;
    ```
    
    → OREDER BY 정렬한 후, WHERE 조건에 맞는 SELECTT 값을 가져오는데 FROM 테이블에 있는 SELECT 값을 가져온다.  
    

  

## INSERT

- INSERT문의 기본 틀
    
    ```sql
    INSERT INTO [스키마.]테이블명 (컬럼1, 컬럼2, ... )
    VALUES (값1, 값2, ...);
    ```
    
- 변형문
    
    ```sql
    INSERT INTO [스키마.]테이블명
    VALUES (값1, 값2, ... );
    
    INSERT INTO [스키마.]테이블명 (컬럼1, 컬럼2, ...)
    SELECT 문;
    ```
    

## UPDATE

- UPDATE문의 기본 틀
    
    ```sql
    UPDATE [스키마.]테이블명
    SET 컬럼1 = 변경값1,
            컬럼2 = 변경값2, ...
    WHERE 조건;
    ```
    
- UDPATE vs AlTER
    
    update → 데이터 값 변환
    alter → 테이블 컬럼명 변환


---
**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**