---
title: Oracle - 게시판 만들기 sql문
date : "2022-07-07"
categories:
- [Sql]
tags:
- [Oracle]
- [Spring]
- [Spring Boot]
---

Spring과 Oracle을 사용해서 게시판 만들기 위해서는 필요에 따라 쿼리문을 작성해야 하는데 이 페이지에서 게시판 만들기 위해서 사용한 쿼리문을 정리해보려 한다.  

### 😀 목차

1. 나만의 스키마 만들기
2. 테이블 생성 및 조회
3. 테이블 수정
4. 데이터 복사
5. 데이터 삭제
6. Rownum과 인덱스

---

## 나만의 스키마 만들기

> 😲 스키마 Schema 란? in Oracle
 우서 스키마는 해당 스키마에 속하고, 연관된 Table들을 한 곳에 모은 일종의 폴더라고 할 수 있다. 
 DB 시스템은 Table에 Data를 CRUD를 할 수 있도록 하는데, 스키마가 이 Table의 묶음인 것이다. 즉, 스키마는 스키마 오브젝트의 묶음이라고 한다. 
> 그리고 오라클은 여러 사용자를 생성 할 수 있는데, 각각의 사용자는 자신이 관리하는 표에 접속이 가능하다.
 최상위 관리자는 SYS로 SYS에서 사용자 생성 한 뒤, 권한을 부여 할 수 있다.
 그 때 동시에 사용자에 속하는 스키마도 같이 만들어진다.


  

다양한 데이터베이스를 지원하는 dbeaver를 사용하여 진행한다.

1. 최상위 관리자 SYS로 스키마 생성 → **SYS** / **SYSDBA** 로 생성
    
    ![](/images/board_sql/Untitled.png)
    

  

1. 최상위 권한에서 사용자 계정 생성하기
    
    ```sql
    -- 1. 유저 생성 문
    -- CREATE USER 아이디 IDENTIFIED BY 비번;
    -- 19c부터 아이디 앞에 c##을 추가해야한다.
    -- CREATE USER c##아이디 IDENTIFIED BY 비번;
    -- 위 과정을 없애기 위해 다음을 실행 후 그냥 생성
    ALTER SESSION SET "_ORACLE_SCRIPT"=TRUE;
    CREATE USER zerobbang IDENTIFIED BY zero123;
    
    -- 유저 삭세
    -- DROP USER zerobbang;
    ```
    
2. CONNECT 권한 및 RESOURCE 권한
    
    ```sql
    -- 2. 권한 주기
    -- with grant option : 유저가 가지게 될 권한을 다른 사람에게 부여할 권한까지 포함한다.
    -- Connect : 접속 권한
    -- Resource : 객체 - 생성, 수정, 삭제 / 데이터 - 입력, 수정, 조회, 삭제
    GRANT CONNECT, dba, resource TO zerobbang;
    
    -- 권한 삭제
    REVOKE CONNECT, dba, resource FROM zerobbang;
    ```
    
3. 사용자 계정 연결
    
    ![](/images/board_sql/Untitled%201.png)
    

  

---

## 테이블 생성

  

### 더미테이블 DUAL로 연결 확인하기

DUAL은 가상의 테이블로 하나의 행, 하나의 컬럼만 갖는 더미 테이블에 속한다.  

그리고 DUAL을 통해서 계산 함수를 실행할 수 있다.

```sql
SELECT * FROM DUAL;
-- 날짜 , 시간 확인 하기
SELECT SYSDATE FROM DUAL;
```

  

### 게시글 테이블 생성

table_board 대신 자신이 테이블 명을 정해서 생성하면 된다.

```sql
create table table_board(
    bno number generated always as IDENTITY,   -- Identity 컬럼을 이용해서 번호 자동 증가
    title varchar2(150) not null,
    content varchar2(2000) not null,
    writer varchar2(50) not null,
    regdate date default sysdate,
    updatedate date default sysdate,
    constraint pk_board PRIMARY key(bno)  -- 제약 조건 걸어주기
);
```

  

- IDENTITY 컬럼
    
    이 컬럼은 하나의 테이블에 하나의 identity 컬럼을 갖을 수 있다.
    
    > 구문 : generated [always|by default [on null]] as identity [(identity_options)]
    > 
    
    Oracle은 always를 입력하지 않아도 자동으로 선택되어서 쿼리문을 실행한다.
    
    그래서 이 컬럼에 대해서 insert or select 문을 실행하면 에러가 발생하는데 by default를 사용하면 실행은 가능하지만 주위가 필요하므로 지양한다.
    

  

### 데이터 입력

```sql
insert into table_board(title, content, writer) values ('테스트 제목1', '테스트 내용1', '작가1');
insert into table_board(title, content, writer) values ('테스트 제목2', '테스트 내용2', '작가2');
insert into table_board(title, content, writer) values ('테스트 제목3', '테스트 내용3', '작가3');
```

😡 주의! - 위에서 설정했던 Identity 컬럼에 값을 입력할 수 없다.

### 테이블 조회

```sql
SELECT * FROM table_board;

-- 총 행 조회
SELECT count(*) from table_board;
```

   

---

## 테이블 수정

```sql
update table_board set title='제목 수정', content='내용 수정', updateDate = sysdate where bno = 8
```

  

---

## 데이터 복사

### 재귀 복사

```sql
insert into table_board(title,content,writer) (select title,content, writer from table_board);
```

원래 기본 insert 문법은 `insert into 테이블 명 ( … ) values ( … );`인데 재귀 복사를 사용할 경우 values를 뺀 위 문법을 사용한다.  

원리 → 전체 조회한 데이터를 다시 해당 테이블에 입력한다.  

  

---

## 데이터 삭제

```sql
delete table 테이블 명 (where 조건 절);

-- 테이블 삭제인 경우
-- DROP TABLE 테이블 명;
```

  

  

---

## Rownum 과 인덱스

Rownum은 실행결과 확인을 통해서 보면 정렬이 되기 전에 매겨지고 정렬이 된다.

**즉, 정렬을 하고 행 번호를 매기는 것이 아니라 번호를 매긴 다음 정렬을 한다.** 

그래서 정렬 한 뒤, 행 번호를 사용하려면 inner 조인을 사용해서 먼저 정렬이 수행되도록 해주어야 한다. 

```sql
SELECT ROWNUM, BNO, TITLE, CONTENT, WRITER, REGDATE, UPDATEDATE
FROM ZEROBBANG.TABLE_BOARD;

SELECT ROWNUM, BNO, TITLE, CONTENT, WRITER, REGDATE, UPDATEDATE 
FROM ZEROBBANG.TABLE_BOARD ORDER BY WRITER;
```

  

### 인덱스와 정렬

인덱스와 정렬의 결과는 같을 지 몰라도 방대한 양의 데이터를 다룰 때는 인덱스를 사용하여 실행해야 비용도 절감되고 속도도 향상 된다.  

 그런데 만약 적은 양의 데이터를 사용한다면 정렬을 사용할 때가 더 비용 절감되고 속도가 더 빠를 수 있다.  인덱스를 사용하게 되면 원본 데이터 양에 비해 인덱스에 할당 되는 용량이 커질 수 있기 때문이다.  

 그래서 인덱스로 항상 사용해야 하는 것이 아니라 상황에 맞게 사용하면 된다.

```sql
-- 1. 힌트를 사용해 인덱스한 쿼리문 ( Rownum1 방식 )
select rn, bno, title, content, writer, regdate, updatedate from(
        select /*+INDEX_DESC(table_board pk_board) */ rownum as rn, bno, title, content, writer, regdate, updatedate
        from table_board)
where rn between 11 and 20;

-- 2. 정렬을 사용한 쿼리문
select rn, bno, title, content, writer, regdate, updatedate from(
        select  rownum as rn, bno, title, content, writer, regdate, updatedate
        from table_board ORDER BY bno DESC)
where rn between 11 and 20;
-- Oracle이 자동으로 index를 추가한다.

-- rownum2 방식
select rn, bno, title, content, writer, regdate, updatedate from(
        select /*+INDEX_DESC(table_board pk_board) */ rownum as rn, bno, title, content, writer, regdate, updatedate
        from table_board where ROWNUM  <=20)
WHERE rn>10;
```

### Rownum 등호 작동 방식

 간단히 말하자면, rownum은 조건절이 만족하면 번호를 부여하고 조건에 맞지 않으면 그 행을 버리는 방식을 갖고 있다.  

 만약 행 번호가 1 ~ 10을 갖고 있는 테이블에서 rownum = 3 의 조건으로 쿼리를 진행하면 아무것도 나오지 않을 것이다.  

 테이블의 첫 행의 행 번호가 3이 아니기 때문에 버려지면, 그 다음 행 번호가 그대로 2인 것이 아니라 다시 1부터 시작기 때문에 행 번호 3을 찾을 수 없어 빈 결과 값이 출력 될 것이다.  

 다른 말로 하자면, rownum = 1은 검색은 가능하나 그 외 숫자와 등호를 사용하면 조건에 맞는 행을 찾지 못한다.  

---

[스키마에 자세히 보려면 [클릭](https://www.hedleyonline.com/ko/blog/%EC%8A%A4%ED%82%A4%EB%A7%88%EC%97%90-%EB%8C%80%ED%95%9C-%EB%AA%A8%EB%93%A0%EA%B2%83-2022/)]

[Identity 컬럼에 대해 자세히 보려면 [클릭](https://m.blog.naver.com/kang_sok/221840061270)]

[rownum 자세히 보려면 [클릭](https://jhnyang.tistory.com/454)]


**_<span style="color:#4682B4;"> 이 블로그는 혼자 공부하며 기록하는 블로그로 잘못된 정보에 대한 의견은 격하게 환영합니다.🤩 </span>_**