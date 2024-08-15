## <p align="center">📆8/2</p>

- 아직 7월이라 생각했는데... 8월 이군요.

### MySql

## 인덱스 생성 및 테이블 변경

```sql
CREATE INDEX index_member ON member(member_name); -- 오타 수정
ALTER TABLE new_table CHANGE memebr_name member_name VARCHAR(4); -- 테이블 칼럼명 수정
SELECT * FROM new_table; -- 테이블 조회

RENAME TABLE memebr TO member; -- 테이블명 수정
```

## 데이터베이스 및 테이블 관리

```sql
CREATE DATABASE shop_db; -- 데이터베이스 생성
RENAME TABLE firstdb.member TO shop_db.member; -- 테이블 이동
RENAME TABLE firstdb.user_table TO shop_db.user; -- 테이블 이름 변경 및 이동
DROP DATABASE firstdb; -- 데이터베이스 삭제
-- 기존에 잘 못 생성한 테이블 이름 을 바꾸며 이동
-- 구조를 처음부터 잘 짜야함을 배움
-- 교재에 없는 것을 많이 체득
```

## 뷰 생성

```sql
CREATE VIEW member_view AS SELECT * FROM member; -- 뷰 생성
```

## 프로시저

```sql
DELIMITER //
CREATE PROCEDURE myProc()
BEGIN
    SELECT * FROM member WHERE member_name = '나훈아'; -- 특정 멤버 조회
    SELECT * FROM user WHERE member_name = '삼각김밥'; -- 특정 유저 조회
END //
DELIMITER ;
```

## 테이블 생성 및 데이터 삽입

```sql
USE market_db;
CREATE TABLE member (
    mem_id CHAR(8) NOT NULL PRIMARY KEY,
    mem_name VARCHAR(10) NOT NULL,
    mem_number INT NOT NULL,
    addr CHAR(2) NOT NULL,
    phone1 CHAR(3),
    phone2 CHAR(8),
    height SMALLINT,
    debut_date DATE
); -- 테이블 생성

INSERT INTO member VALUES('NEWJ', '뉴진스', 5, '서울', '82', 1234567, 170, '2022-07-01'); -- 데이터 삽입
SELECT * FROM market_db.member; -- 테이블 조회
```

## 조회 및 필터링

```sql
SELECT addr AS 주소, debut_date AS "데뷔 일자", mem_name FROM member; -- 컬럼 별칭 사용

SELECT 열_이름
FROM 테이블_이름
WHERE 조건식; -- 조건에 따른 조회

SELECT mem_name, height, mem_number
FROM member
WHERE height >= 160; -- 키가 160 이상인 멤버 조회

SELECT mem_name, height, mem_number
FROM member
WHERE height >= 160 AND mem_number > 6; -- 키가 160 이상이면서 멤버 번호가 6보다 큰 멤버 조회

SELECT 열_이름
    FROM 테이블_이름
    WHERE 조건식
    GROUP BY 열_이름
    HAVING 조건식 -- 그룹화 후 조건
    ORDER BY 열_이름
    LIMIT 숫자; -- 결과 제한
```

## 내부조인

- 🖨️ 모두 있는 내용만 출력

```sql
SELECT <Col_list>
FROM <1stT>
	INNER JOIN <2ndT>
	ON <conditional>
[WHERE search_conditional]
```

```sql
USE market_db;
SELECT * 
	FROM buy
	INNER JOIN member
	ON buy.mem_id = member.mem_id	
WHERE buy.mem_id = 'GRL';
-- '7', 'GRL', '혼공SQL', '서적', '15', '5', 'GRL', '소녀시대', '8', '서울', '02', '44444444', '168', '2007-08-02'
```


### 별칭을 붙여 가독성 개선

```sql
SELECT B.mem_id, M.mem_name, B.prod_name, M.addr, CONCAT(M.phone1, M.phone2), '연락처' 
	FROM buy B
	INNER JOIN member M
	ON B.mem_id = M.mem_id	
ORDER BY M.mem_id;

-- 'APN', '에이핑크', '아이폰', '경기', '03177777777', '연락처'
-- 'APN', '에이핑크', '혼공SQL', '경기', '03177777777', '연락처'
-- 'APN', '에이핑크', '청바지', '경기', '03177777777', '연락처'
-- 'APN', '에이핑크', '혼공SQL', '경기', '03177777777', '연락처'
-- 'BLK', '블랙핑크', '지갑', '경남', '05522222222', '연락처'
-- 'BLK', '블랙핑크', '맥북프로', '경남', '05522222222', '연락처'
-- 'BLK', '블랙핑크', '청바지', '경남', '05522222222', '연락처'
-- 'GRL', '소녀시대', '혼공SQL', '서울', '0244444444', '연락처'
-- 'MMU', '마마무', '아이폰', '전남', '06199999999', '연락처'
-- 'MMU', '마마무', '에어팟', '전남', '06199999999', '연락처'
-- 'MMU', '마마무', '지갑', '전남', '06199999999', '연락처'
-- 'MMU', '마마무', '지갑', '전남', '06199999999', '연락처'
```

### 중복된 결과 1개만 출력하기

```sql
SELECT DISTICT
```


### 외부 조인

- 한쪽 테이블에만 있어도 결과 추출 할 때 

```sql
SELECT <Col_list>
FROM <1st T(left)>
    <LEFT || RIGHT || FULL> OUTER JOIN <2ndT(RIGHT)>
	ON <conditional>
[WHERE search_conditional];
```


### LEFT JOIN

- 왼쪽 테이블을 모두 출력한다

```sql
SELECT M.mem_id, M.mem_name, B.prod_name, M.addr
	FROM buy B
	LEFT OUTER JOIN member M
	ON M.mem_id = B.mem_id	
ORDER BY M.mem_id;
```

### RIGHT JOIN

- 오른쪽 테이블을 모두 출력한다

```sql
SELECT M.mem_id, M.mem_name, B.prod_name, M.addr
	FROM buy B
	LEFT OUTER JOIN member M
	ON M.mem_id = B.mem_id	
ORDER BY M.mem_id;
```


### 기타조인: 상호조인

### CROSS JOIN
- cartesian product
    - on 구문 사용할 수 없음
    - 내용은 의미 X, 랜덤조회
    - 테스트용 대용량 조회 목적

```sql
SELECT * 
    FROM buy
    CROSS JOIN member;
```

### 자체조인 

### Self join

- 1개로 조인 하는 것


```sql
SELECT <Col_list>
FROM <Table> alias A
    INNER JOIN <TABLE> alias B
	ON <conditional>
[WHERE search_conditional];
```