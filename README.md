
# 1. 데이터베이스의 개념
- DataBase(DB)   
여러 사람에 의해 공유되어 사용될 목적으로 통합하여 관리되는 데이터의 집합   
- DataBase Management System(DBMS)   
다수의 사용자들이 데이터베이스 내의 데이터를 접근할 수 있도록 해주는 소프트웨어 도구의 집합   
- SQL(Structured Query Language)   
관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어   
   - DML   
   Data Manipulation Language의 약자. Table의 행을 검색하거나 변경하기 위한 것   
   `SELECT`: Table 행을 검색   
   `INSERT`: Table에 신규 행을 등록   
   `DELETE`: Table에 행을 삭제
   - DDL   
   Data Definition Language의 약자.  데이터를 저장하는 DB 및 Table을 생성, 삭제하기 위한 것   
   `CREATE`: DB or Table등을 작성   
   `DROP`: DB or Table 등을 삭제   
   `ALTER`: DB or Table 등의 구성 변경
   - DCL
   Data Control Language의 약자. DB에서 처리한 변경 내용을 확정하거나 취소하기 위한 것이다. 또한 RDBMS 사용자에게 처리 권한을 부여하기도 한다.   
   `COMMINT`: DB 변경 내용을 확정   
   `ROLLBACK`: DB 변경 내용을 취소   
   `GRANT`: 사용자에게 처리 권한을 부여   
   `REVOKE`: 사용자에게 처리 권한을 제거   
![1](https://user-images.githubusercontent.com/47620799/80223458-484c0200-8683-11ea-8a21-e019b1e58f12.PNG)
- 데이터베이스의 종류 
   - 계층형 데이터베이스: 폴더와 파일 등의 계층 구조로 데이터를 저장하는 방식   
   - 관계형 데이터베이스: 키(key)와 값(value)들의 간단한 관계를 테이블화하여 데이터를 저장하는 방식
   - 객체지향 데이터베이스: 객체 지향 개념 도입하여 계층에 따라 데이터 구조를 표현하고 데이터와 조작 절차를 다루는 방식   
   - XML 데이터베이스: XML 형식으로 기록된 데이터를 저장하는 방식 XQuery 사용   
   - 키-밸류 스토어(KVS): 키와 그에 대응하는 값(밸류)라는 단순한 형태의 데이터를 저장하는 데이터베이스 NoSQL이라는 슬로건으로부터 생겨난 데이터베이스로, 열 지향 데이터베이스라고도 부른다.   
- 클라이언트/서버 모델   
사용자 조작에 따라 요청을 전달하는 클라이언트와 해당 요청을 받아 처리하는 서버로 소프트웨어를 나누고, 복수의 컴퓨터 상에서 하나의 모델을 구현하는 시스템   
   
# 2. SQL(명령어 대소문자 구분 없음 구분을 위해 대문자로 기입)    
1. DATABASE 생성  
`CREATE DATABASE <이름>;`   
`CREATE DATABASE test;`   
   
2. DATABASE 사용   
`USE <DB 명>`   
`USE test;`
   
3. TABLE 생성   
```
CREATE TABLE <이름> 
( <열 이름1> <데이터타입> <열의 제약>, 
  <열 이름2> <데이터타입> <열의 제약>,
  <열 이름3> <데이터타입> <열의 제약>, 
  ...
  <이 table의 제약1>, <이 table의 제약2>, ...
  );
  ```
  
  
  ```
  CREATE TABLE test 
( no           INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name         VARCHAR(10)  NOT NULL,
  birthday     DATE NOT NULL,
  address      VARCHAR(100)  NOT NULL,
);
```   
데이터 타입   
- INTEGER or INT: 정수를 나타냄   
- CHARACTER or CHAR: 문자열형의 하나로 문자열을 저장 (길이)를 명시해야 함   
- VARCHAR: 길이 255개까지의 문자 데이터 저장 CHAR과 동일하게 (길이)를 명시해야 함   
- BLOB: 큰 덩어리의 문자 데이터   
- DEC: DECIMAL의 약어, 십진수   
- DATE: 날짜(시간은 다루지 않음)   
- DATETIME or TIMESTAMP: 데이터 베이스 시스템에 따라 앞의 둘중 하나로 사용하며 날짜와 시간을 사용   
- TIME: 시간만 사용
4. TABLE 정보 확인   
`DESC <Table 명>;`   
`DESC test;`   
5. TABLE 삭제   
`DROP TABLE <Table 명>;`   
`DROP TABLE test;`   
`TRUNCATE TABLE <teble 명>;` : 테이블 내의 전체 행 삭제   
6. TABLE 데이터 입력   
`INSERT INTO <TABLE 명> (열 이름1, 열 이름2, 열 이름3, ...) VALUES ('값1', '값2', '값3',...);`   
`INSERT INTO test (name, birthday, address) VALUES ('david', '1991-01-06', 'SungNam, Korea');`   
TABLE 변경(추가)   
`ALTER TABLE <테이블명> <변경명령>;`   
`ALTER TABLE <테이블명> ADD <열정의>;`: 테이블에 열 추가   
`ALTER TABLE <테이블명> MODIFY <열 정의>;`:열 속성 변경   
`ALTER TABLE <테이블명> CHANGE <기존 열이름> <변경 열이름>;`:열의 이름 변경   
`ALTER TABLE <테이블명> DROP <열명>;`: 열 삭제   
7. DATABASED 데이터 읽기   
`SELECT * FROM <TABLE 명>;`   
`SELECT * FROM test;`   
*(이터리스크)는 모든열을 의미하는 메타문자   
8. 검색 조건 지정  
데이터 검색에는 열을 지정하는 방법과 행을 지정하는 방법이 있다.   
행을 선택할 때는 WHERE, 열을 선택할 때는 SELECT 사용  
- SELECT 열 지정   
`SELECT <열1, 열2, ..> FROM <테이블 명>`   
`SELECT name, address FROM test;`   
- WHERE 행 지정   
*수치형 열을 제외한 문자열형은 싱글쿼트('')로 둘러싸 표기한다. 날짜시간형의 경우도 동일하다 연원일을 하이픈(-), 시분초를 콜론(:)으로 구분
`SELECT <열1, 열2, ...> FROM <테이블 명> WHERE <조건식>;`   
`SELECT * FROM test WHERE name='selly';`   

- NULL 값 검색   
` SELECT <열1, 열2, ...> FROM <테이블 명> WHERE <열> IS NULL;`   
` SELECT * FROM test WHERE name IS NULL;`   

- 비교 연산자   
   - `=` : 좌변과 우변의 값이 같으면 참   
   - `<>`: 좌변과 우변의 값이 같지 않을 경우 참   
   - `>` : 좌변 값이 우변의 값보다 클 경우 참   
   - `<` : 좌변의 값이 우변의 값보다 작을 경우 참   
   - `>=`: 좌변의 값이 우변의 값보다 크거나 같을 경우 참   
   - `<=`: 좌변의 값이 우변의 값보다 작거나 같을 경우 참   
   
9. 조건 조합   
SELECT 명령을 사용해서 데이터베이스에서 데이터를 검색할 때 단순한 조건식을 넣으면 많은 결괏값이 반환되어 한눈에 알아보기 힘들기 때문에   
2개 이상의 조건식을 조합해 검색하는 경우가 많다. 조합할 때는 `AND`, `OR`, `NOT` 3가지 방법을 사용한다.   
- AND 조합   
좌/우의 식 모두 참일 경우 AND 연산자는 참을 반환   
`조건식1 AND 조건식2`   
```
CREATE TABLE test1  
(no int not null auto_increment primary	key,
 a     int, 
 b     int, 
 c     int,
 d     int);
```   
 
```
insert into test1 (a, b, c, d) values ( 2, 0, 1, 0);
insert into test1 (a, b, c, d) values ( 1, 2, 0, 0);
insert into test1 (a, b, c, d) values ( 0, 1, 1, 0);
insert into test1 (a, b, c, d) values ( 1, 0, 0, 0);
insert into test1 (a, b, c, d) values ( 1, 0, 0, 1);
insert into test1 (a, b, c, d) values ( 2, 0, 2, 0);
insert into test1 (a, b, c, d) values ( 5, 0, 2, 2);
insert into test1 (a, b, c, d) values ( 4, 2, 2, 0);
insert into test1 (a, b, c, d) values ( 3, 0, 0, 1);
```
 `SELECT * FROM test1 WHERE a<>0 AND b <>0;`   
 - OR 조합   
 좌/우의 식 어느 쪽이든 조건을 만족하면 결과는 참   
 `조건식1 OR 조건식2`   
 `SELECT * FROM test1 WHERE a<>0 OR c <>0;`   
 - AND 와 OR 조합하여 사용하기   
 `SELECT * FROM test1 WHERE a=1 OR a=2 AND b=1 OR b=2;`   
 *OR보다 AND의 우선순위가 높기 떄문에 a=2 AND b=1이 먼저 계산된다. 괄호로 나타내면 아래와 같다.   
 `WHERE a=1 OR (a=2 AND b=1) OR b=2`   
- NOT 조합   
NOT 연산자는 오른쪽에만 항목을 지정하는 '단항 연산자', 오른쪽에 지정한 조건식의 반대 값을 반환한다.    
`SELECT * FROM test1 WHERE NOT(a<>0 OR b=2);`   

10. 패턴 매칭에 의한 검색   
`LIKE`를 사용하면 문자열의 일부분을 비교하는 부분 검색을 할 수 있다.(ctrl+F의 개념 정도..)   
= 연산자로 검색할 경우에는 열 값이 완전히 일치할 때 참이 된다. LIKE를 사용하면 열 값이 부분적으로 일치하는 경우에도 참이 된다.   
패턴을 정의할 때는 `%`와 `_`의 메타문자(와일드카드라고도 불림)를 사용   
`%`는 임의의 문자열을 의미, `_`는 임의의 문자 하나를 의미   
```
CREATE TABLE test2   (no int not null auto_increment primary key,  text varchar(100));
insert into test2 (text) values ( 'SQL은 RDBMS를 조작하는 언어이다.');
insert into test2 (text) values ( 'LIKE에서는 메타문자 %와_를 사용할 수 있다.');
insert into test2 (text) values ( 'LIKE는 SQL에서 사용할 수 있는 술어 중 하나이다.');
```   
- 문자열 SQL을 포함하는 행을 패턴 매칭으로 검색   
`SELECT * FROM test2 WHERE text LIKE 'SQL%';`  
3번째 행에도 SQL이 있는데 검색되지 않았다.   
`SQL%`: 전방일치(SQL은 RDBMS를...), `%SQL%`: 중간일치(LIKE는 SQL에서 사용..), `%SQL`: 후방일치(입문 SQL)   
- LIKE로 % 검색   
test2의 두번째 행은 데이터 안에 `%`와 `_`를 포함하는데 해당 경우는 이스케이프(\)를 사용한다.   
`SELECT * FROM test2 WHERE text LIKE '%\%%';`   
-문자열 상수 '의 이스케이프   
메타문자와 같이 문자열 상수를 검색할 때도 같은 문제가 발생한다.   
문자열 상수는 '문자열'과 같이 '로 둘러싸 표기한다. 예를들어 'It's'라는 문자열을 문자열 상수로 표기하면   
`'It''s'`   
11. 정렬 ORDER BY   
SELECT 명령의 ORDER BY를 사용하여 정렬(검색 조건이 필요없는 경우에는 WHERE를 생략)   
`SELECT 열명 FROM 테이블명 WHERE 조건식 ORDER BY 열명`   

```
CREATE TABLE test3 ( name varchar(10) not null, age int not null, address varchar(50) not null);
INSERT INTO test3 (name, age, address) VALUES ('A', 34, 'Daegu, Korea');
INSERT INTO test3 (name, age, address) VALUES ('B', 28, 'Seoul, Korea');
INSERT INTO test3 (name, age, address) VALUES ('C', 18, 'Busan, Korea');
INSERT INTO test3 (name, age, address) VALUES ('D', 21, 'Daegu, Korea');
SELECT * FROM test3;
```   
- age 열로 정렬하기   
`SELECT * FROM test3 ORDER BY age;`   

- 내림차순 정렬   
`SELECT <열명> FROM <테이블명> ORDER BY <열명> DESC`   
`SELECT * FROM test3 ORDER BY age DESC;`   
- 오름차순 정렬   
`SELECT <열명> FROM <테이블명> ORDER BY <열명> ASC`   
`SELECT * FROM test3 ORDER BY age ASC;`   
   
- 복수열 정렬   
`SELECT <열명> FROM <테이블명> ORDER BY <열명1, 열명2, ...>`   
```
CREATE TABLE test4 (a int, b int, c int);
INSERT INTO test4 (a, b, c) VALUES (1, 1, 3);
INSERT INTO test4 (a, b, c) VALUES (1, 3, 1);
INSERT INTO test4 (a, b, c) VALUES (1, 2, 2);
INSERT INTO test4 (a, b, c) VALUES (2, 1, 1);
INSERT INTO test4 (a, b, c) VALUES (3, 2, 1);
```   
`SELECT * FROM test4 ORDER BY a;`   
`SELECT * FROM test4 ORDER BY b;`   
`SELECT * FROM test4 ORDER BY a, b;`   
`SELECT * FROM test4 ORDER BY b, a;`   
- 정렬 방법 지정   
`SELECT <열명> FROM <테이블명> ORDER BY <열명1<ASC/DESC>, 열명2<ASC/DESC>, ...>`   
`SELECT * FROM test4 ORDER BY a ASC, b DESC`   
- NULL 값 정렬   
MYSQL의 경우 NULL 값은 가장 작은 값으로 취급해 ASC(오름차순)에서는 가장 먼저, DESC(내림차순)에서는 가장 나중에 표시   
12. 결과 행 제한   
SELECT 명령에서 결괏값으로 반환되는 행을 제한할 수 있음   
`SELECT <열명> FROM <테이블명> LIMIT <행수> (OFFSET<시작행>)`   
```
CREATE TABLE test5  
(no int not null auto_increment primary key, a int, b int);
INSERT INTO test4 (a, b) VALUES (1, 1);
INSERT INTO test4 (a, b) VALUES (1, 3);
INSERT INTO test4 (a, b) VALUES (1, 2);
INSERT INTO test4 (a, b) VALUES (2, 1);
INSERT INTO test4 (a, b) VALUES (3, 2); 
```   
`SELECT * FROM test5 LIMIT 3;`   
`SELECT * FROM test5 LIMIT 2 OFFSET 1;`   
`SELECT * FROM test5 LIMIT 3 OFFSET 2;`   
- 정렬후 제한   
`SELECT * FROM test5 ORDER BY a DESC LIMIT 4;`   
`SELECT * FROM test5 ORDER BY a DESC LIMIT 4 OFFSET 1;`   
13. 수치연산   
SQL은 데이터베이스를 조작하는 언어이지만 컴퓨터를 조작하는 어너이기도 한 만큼 기본적으로 계산 기능을 포함한다.    
- 사칙연산   
`+`:덧셈   
`-`:뺄셈   
`*`:곱셈   
`/`:나눗셈   
`%`:나머지   
- 연산자의 우선 순위   
1순위: `*`, `/`, `%`   
2순위: `+`, `-`   
`1-2+3`: 우선 순위가 같다면 왼쪽에서 오른쪽으로 계산   
`1+(2*3)`: `+`보다 `*`의 우선 우선 순위가 높으므로 `*`부터 계산   
- SELECT 구로 연산하기   
`SELECT <식1, 식2, ...> FROM <테이블명>`   
```
CREATE TABLE test6  
(no int not null auto_increment primary key, price int, quantity int);
INSERT INTO test6 (price, quantity) VALUES (1000, 10);
INSERT INTO test6 (price, quantity) VALUES (2000, 8);
INSERT INTO test6 (price, quantity) VALUES (1500, 11);
INSERT INTO test6 (price, quantity) VALUES (3100, 6);
INSERT INTO test6 (price, quantity) VALUES (500, 7);
```
`SELECT *, price*quantity FROM test6;`
- 열의 별명   
SELECT 결과에서 price * quantity라고 명명된 열이 금액을 계산한 부분인데 해당 price * quantity 같이 열 이름이 길고 알아보기 어려운 경우   
별명(alias)을 붙여 열명을 재지정할 수 있다.   
`SELECT <식1, 식2, ...> AS <별명> FROM <테이블 명>;`   
`SELECT *, price*quantity AS amount FROM test6;`   
`SELECT *, price*quantity 'amount' FROM test6;`: AS를 생략할 수 있다.   
데이터베이스 객체명 = "객체명", 문자열 상수 = '상수'   
- WHERE 구에서 계산, 검색하기   
ex)WHERE 구에서 금액을 계산하고 10000원 이상인 행 검색하기   
`SELECT*, price*quantity AS amount FROM test6 WHERE price*quantity >=10000;`   
- NULL 값의 연산   
SQL에서 NULL 값은 0이 아닌 NULL이다. `NULL+1`, `NULL*2`, `NULL/3` 등 모든 연산의 결과는 NULL이다.   
-ORDER BY 구에서의 연산   
`SELECT*, price*quantity AS amount FROM test6 ORDER BY (price*quantity) or (amount) DESC;`: 내림차순 정렬 연산식이나 별명 모두 사용가능   
`SELECT*, price*quantity AS amount FROM test6 ORDER BY (price*quantity) or (amount) ASC;`: 올림차순 정렬 연산식이나 별명 모두 사용가능   
14. 문자열 연산   
-문자열 결합   
`+`: 문자열 결합, SQL Sever에서 사용   
`||`: 문자열 결합, Oracle, DB2, PostgreSQL에서 사용   
`CONCAT`: 문자열 결합, Mysql에서 사용   
```
CREATE TABLE test7  
(no int not null auto_increment primary key, price int, quantity int, unit varchar(10));
INSERT INTO test7 (price, quantity, unit) VALUES (1000, 10, '개');
INSERT INTO test7 (price, quantity, unit) VALUES (2000, 8, '캔');
INSERT INTO test7 (price, quantity, unit) VALUES (1500, 11, '묶음');
INSERT INTO test7 (price, quantity, unit) VALUES (3100, 6, '봉지');
INSERT INTO test7 (price, quantity, unit) VALUES (500, 7, 'KG');
```   
`SELECT CONCAT(quantity, unit) FROM test7;`   
- SUBSTRING   
`SUBSTRING`함수는 문자열의 일부분을 계산해서 반환해주는 함수   
`SUBSTRING('20190121001',1, 4);`: 2019      
`SUBSTRING('20190121001',5, 2);`: 01   
- TRIM   
문자열의 앞뒤로 여분의 스페이스가 있을 경우 이를 제거해주는 함수로 문자열 도중에 존재하는 스페이스는 제거되지않는다.   
`TRIM('ABC    ')`='ABC'   
- CHARACTER_LENTH   
문자열의 길이를계산해 돌려주는 함수 
15. 날짜 연산   
- 시스템 날짜   
컴퓨터에는 반드시 시계가 내장되어 있다. 네트워크나 주변기기와 데이터 통신을 하기 위해서는 시간을 정확하게 측정할 필요가 있다.   
표준 SQL에서는 `CURRENT_TIMESTAMP`의 함수를 사용한다.   
`SELECT CURRENT_TIMESTAMP;`   
- 날짜의 덧셈과 뺄셈   
날짜 시간형 데이터는 기간형 수치데이터와 덧셈 및 뺼셈을 할 수 있다.   
날짜 시간형 데이터에 기간형 수치데이터를 더하거나 빼면 날짜 시간형 데이터가 반환된다.   
`SELECT CURRENT_DATE + INTERVAL 1 DAY;`: 날짜를 연산해 시스템 날짜의 1일 후를 검색   
`SELECT CURRENT_DATE - INTERVAL 1 DAY;`: 날짜를 연산해 시스템 날짜의 1일 전을 검색   
16. CASE 문으로 데이터 변환   
RDBMS에 준비된 함수를 사용해 데이터를 특정 형태로 변환하는 경우도 있지만, 임의의 조건에 따라 독자적으로 변환 처리를 지정해 데이터를 변환하고 싶은 경우도 있다.(EX) NULL 값을 0으로 간주하여 계산 등) 이때, CASE 문을 사용한다.   
```
CASE WHEN <조건식1> THEN <식1> 
(WHEN <조건식 2> THEN <식2> ...)
(ELSE 식3)
END
```
```
CREATE TABLE test8  
(no int not null auto_increment primary key, a int);
INSERT INTO test8 (a) VALUES (NULL);
INSERT INTO test8 (a) VALUES (1);
INSERT INTO test8 (a) VALUES (3);
INSERT INTO test8 (a) VALUES (5);
INSERT INTO test8 (a) VALUES (NULL);
```   
`SELECT a, CASE WHEN a IS NULL THEN 0 ELSE a END "a(null=0)" FROM test8;`   
CASE 문에는 2개의 구문이 있다. 검색 CASE와 단순 CASE의 두 개 구문으로 나눌 수 있다.   
검색 CASE : `CASE WHEN <조건식> THEN <식>`   
단순 CASE : `CASE 식1 WHEN 식2 THEN 식3 ... END`   
성별 코드 변환하기 검색, 단순 CASE   
```
CREATE TABLE test9  
(no int not null auto_increment primary key, a int);
INSERT INTO test9 (a) VALUES (1);
INSERT INTO test9 (a) VALUES (1);
INSERT INTO test9 (a) VALUES (2);
INSERT INTO test9 (a) VALUES (2);
INSERT INTO test9 (a) VALUES (1);
INSERT INTO test9 (a) VALUES (null);
```   
```
검색 CASE
SELECT a As "code",
CASE 
 WHEN a=1 THEN 'man'
 WHEN a=2 THEN 'woman'
 ELSE '?'
END AS "sex" FROM test9;
```
```
단순 CASE
SELECT a AS "code",
CASE a
 WHEN 1 THEN 'man'
 WHEN 2 THEN 'woamn'
 ELSE 'NONE'
END AS "sex" FROM test9;
```
ELSE를 생략하면 ELSE NULL이 된다. 따라서 ELSE를 생략하지 않고 지정하는 것이 좋다.   
- COALESCE   
NULL 값을 변환하는 경우라면 `COALESCE`를 사용하는 편이 더 쉽다.해담 함수는 여러 개의 함수를 지정할 수 있다.   
`SELECT a, COALESCE(a,0) FROM test8;`   
17. DELETE   
DB의 테이블에서 행을 삭제하기 위해서 `DELETE` 명령 사용한다.   
`DELETE FROM <테이블명> WHERE <조건식>;`   
- 물리삭제와 논리삭제   
데이터베이스에서 데이터를 삭제하는 방법은 용도에 따라 크게 물리삭제와 논리삭제의 두 가지로 나뉜다.   
하지만, 물리삭제와 논리삭제는 전용 SQL 명령이 따로 존재하지 않다. 해당 내용은 시스템 설계 분야에 관한 것으로, 시스템을 구축할 때   
자주 사용하는 말이다.   
먼저, 물리 삭제는 SQL의 `DELETE` 명령을 사용해 직접 데이터를 삭제하는 방식으로 삭제 대상 데이터는 필요없는 데이터이므로 `DELETE` 명령을   
실행해 테이블에 삭제하는 방식 (예를 들어 SNS와 같은 사용 자의 개인 정보를 다루는 시스템에서 회원탈퇴와 같은 경우에 사용)   
논리 삭제의 경우, 테이블에 '삭제플레그'와 같은 열을 미리 준비해 실제로 행을 삭제하는 대신, `UPDATE` 명령을 사용해 삭제 플래그의 값을   
유효하게 갱신해두자는 발상의 방식으로 실제 테이블 안에 데이터는 남아있지만, 참조할 때에는 삭제플래그가 삭제로 설정된 행을 제외하는   
`SELECT` 명령을 실행한다. 결과적으로는 해당 행이 삭제된 것처럼 보인다.   
(예를 들어 쇼핑몰의 사용자의 주문취소 같은 경우에 사용하여 주문 관련 통계를 낼 때 유용하게 사용)   
18. UPDATE   
DB의 테이블에서 저장되어 있는 값을 갱신하려면 `UPDATE` 명령을 사용한다.   
`UPDATE <테이블명> SET <열1 = 값1, 열2 = 값2,...> WHERE <조건식>;`   
```
SELECT * from test9;
UPDATE test9 SET a=1 WHERE no=3;
```
18. 집계와 서브쿼리   
SQL은 데이터베이스라 불리는 데이터의 집합을 다루는 언어로 집합의 개수나 합계가 궁금하다면 집계함수를 사용하여 간단하게 구할수 있다.   
대표적인 집계 함수는 아래와 같이 5개를 꼽을 수 있다.   
`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`   
- COUNT
행 개수 구하기   
```
CREATE TABLE test10  
(no int not null auto_increment primary key, a int);
INSERT INTO test10 (a) VALUES (10);
INSERT INTO test10 (a) VALUES (5);
INSERT INTO test10 (a) VALUES (7);
INSERT INTO test10 (a) VALUES (3);
INSERT INTO test10 (a) VALUES (15);
INSERT INTO test10 (a) VALUES (21);
```   
`SELECT COUNT(*) FROM test10;`   
`SELECT COUNT(*) FROM test10 WHERE a>=10;`   
- SUM   
합계   
`SELECT SUM(a) FROM test10;`   
- AVG   
평균   
`SELECT AVG(a) FROM test10;`   
`SELECT AVG(CASE WHEN a IS NULL THEN 0 ELSE a END) AS avgnull0 FROM test10;`   
- MIN, MAX   
최솟값, 최댓값   
`SELECT MIN(a), MAX(a) FROM test10;`   
- 그룹화   
`GROUP BY` 구를 사용하여 집계 함수로 넘겨줄 집합을 그룹으로 나눈다. 이와 같은 그룹화를 통해 집계함수의 활용범위를 넓힐수 있다.   
`SELECT * FROM <테이블명> GROUP BY <열1, 열2, ..>`   
```
create table test11(no int not null auto_increment primary key, name varchar(10), quantity int);
INSERT INTO test11 (name, quantity) VALUES ('A', 1);
INSERT INTO test11 (name, quantity) VALUES ('A', 3);
INSERT INTO test11 (name, quantity) VALUES ('B', 1);
INSERT INTO test11 (name, quantity) VALUES ('B', 2);
INSERT INTO test11 (name, quantity) VALUES ('A', 5);
INSERT INTO test11 (name, quantity) VALUES ('C', 3);
SELECT * FROM test11;
```
- name 열로 그룹화하기   
GROUP BY 구에 열을 지정하여 그룹하하면 지정된 열의 값이 같은 행이 하나의 그룹으로 묶인다.   
`SELECT name FROM test11 GROUP BY name;`   
- name 열을 그룹화해 계산하기   
`SELECT name, COUNT(name), SUM(quantity) FROM test11 GROUP BY name;`   
- HAVING 구로 조건 지정   
`HAVING` 구를 사용하면 집계함수를 사용하여 조건식을 지정할 수 있다.   
`SELECT name, COUNT(name) FROM test11 GROUP BY name HAVING COUNT(name) =2;`   
- 결과 값 정렬   
`GROUP BY`로 그룹화해도 실행 결과 순서를 정렬할 수는 없다. 하지만, `ORDER BY`를 사용해 정렬할 수 있다.   
`SELECT name, COUNT(name), SUM(quantity) FROM test11 GROUP BY name ORDER BY SUM(quantity) DESC;`   
- 서브쿼리   
서브쿼리는 SELECT 명령에 의한 데이터 질의로, 상부가 아닌 하부의 부수적인 질의를 의미한다.   
특히, 서브쿼리는 SQL 명령의 `WHERE`구에서 주로 사용된다. `WHERE`구는 `SELECT`, `DELETE`, `UPDATE`구에서 사용한다.   
- DELETE의 WHERE 구에서 서브쿼리 사용   
```
create table test12(a int);
INSERT INTO test12 (a) VALUES (10);
INSERT INTO test12 (a) VALUES (20);
INSERT INTO test12 (a) VALUES (50);
INSERT INTO test12 (a) VALUES (70);
INSERT INTO test12 (a) VALUES (90);
SELECT MIN(a) FROM test12;
```   
최솟값을 가지는 행 삭제하기   
(workbench edit-preferences-sql editor에서 safe updates 체크해제후 진행할 것)   
`DELETE FROM test12 WHERE a =(SELECT * FROM (SELECT MIN(a) FROM test12) tmp );`   
- 스칼라 값   
`SELECT` 명령이 하나의 값만 반환하는 것을 스칼라 값을 반환한다고 한다.   
서브쿼리의 패턴   
패턴1 하나의 값을 반환하는 패턴   
`SELECT MIN(a) FROM test12;`   
패턴2 복수의 행이 반환되지만 열은 하나인 패턴   
`SELECT a FROM test12;`   
패턴3 하나의 행이 반환되지만 열이 복수인 패턴   
`SELECT MIN(a), MAX(a) FROM test12;`   
패턴4 복수의 행, 복수의 열이 반환되는 패턴   
`SELECT * FROM test12;`   
- SELECT 구에서 서브쿼리 사용   
`SELECT (SELECT COUNT(*) FROM test12) AS sq1, (SELECT COUNT(*) FROM test11) AS sq2;`   
- SET 구에서 서브쿼리 사용   
`UPDATE test12 SET a=(SELECT * FROM (SELECT MAX(a) FROM test12) tmp );`   
- FROM 구에서 서브쿼리 사용   
`SELECT * FROM (SELECT * FROM test12)sq;`   
- INSERT 서브쿼리  
`create table test13(a int, b int);`   
`insert into test13 values ( (select count(*) from test11), (select count(*) from test12) );`   
19. 인덱스 구조   
인덱스는 테이블에 붙여진 색인이라 할 수 있다. 인덱스의 역할은 검색속도의 향상이다. 인덱스는 테이블과는 별개로 독립된 데이터베이스 객체로 작성된다.   
테이블을 삭제하면 인덱스도 같이 삭제된다.   
- 검색에 사용하는 알고리즘   
대량의 데이터를 효율적으로검색하는 방법에관해서는 에전부터 여러가지로 연구되어 왔다. 데이터 탐색, 검색 알고리즘 등이 그에 해당한다.   
대표적인 검색 알고리즘은 이진트리가 있으며 그 다음으로 해시가 유명하다.   
- 풀 테이블 스캔(Full Table Scan)   
인덱스가 지정되지 않은 테이블을 검색할 때는 풀 테이블 스캔이라 불리는 검색 방법을 사용한다. 처리 방법은 테이블에 저장된 모든 값을 처음부터 차례로 조사하는 방법이다.   
- 이진 탐색(binary serach)   
이진 탐색은 차례로 나열된 집합에 대해 유효한 검색 방법이다. 처음부터 순서대로 조사하는 것이 아니고 집합을 반으로 나누어 조사하는 검색 방법이다.   
- 이진 트리(binary tree)   
이진 탐색은 고속으로 검색할 수 있는 탐색 방법이지만 데이터가 미리 정렬되어 있어야한다. 하지만, 테이블 내의 행을 언제나 정렬된 상태로 두는 것은   
힘들다. 일반적으로는 테이블에 인덱스를 작성하면 테이블 데이터와 별개로 인덱스용 데이터가 저장장치에 만들어진다. 이때 이진 트리라는 데이터 구조로 작성된다.    
- 인덱스 작성과 삭제   
`CREATE INDEX` , `DROP INDEX`   
`CREATE INDEX <인덱스명> ON <테이블명> (열 명1, 열명2, 열명3,...);`   
`DROP INDEX <인덱스명> ON <테이블명>;`   
20. 뷰 작성과 객체   
뷰는 `SELECT` 명령을 기록하는 데이터베이스 객체, 뷰는 테이블처럼 취급할 수 있지만 실체가 존재하지 않는다는 의미로 가상테이블이라 불리기도 함   
`CREATE VIEW <뷰명> AS SELECT <명령>`   
`CREATE VIEW viewtest AS SELECT * FROM test11;`   
`SELECT * FROM viewtest;`   
`DROP VIEW <뷰명>`   
`DROP VIEW viewtest;`   
21. 복수의 테이블 다루기   
- 집합연산   
`UNION`: 합집합   
```
SELECT * FROM test10;
UNION
SELECT * FROM test12 (ORDER BY <열명>);
```   
`UNION` 을 사용하면 중복을 제거한 뒤 값을 나타낸다.   
`UNION ALL`: 중복 추가   
```
SELECT * FROM test10;
UNION ALL
SELECT * FROM test12 (ORDER BY <열명>);
```   
- 테이블 결합   
테이블의 집합 연산에서는 행 방향으로 데이터가 늘어나거나 줄어드는 계산 진행했다.   
이제부터는 열 방향으로 데이터가 늘어가는 방법이다.   
- 곱집합과 교차결합   
곱집합   
![220px-Cartesian_Product_qtl1 svg](https://user-images.githubusercontent.com/47620799/80581038-81032700-8a47-11ea-9270-0df2ba60c301.png)
교차결합   
데이터베이스의 테이블은 집합의 한 종류라 볼 수 있다. 만약 `SELECT` 명령의 `FROM` 구에 테이블을 두 개 지정하면 이들은 곱집합으로 계산된다.
`SELECT * FROM <테이블명1, 테이블명2>;`
```
create table test15(x varchar(5) );
insert into test15 values ('A');
insert into test15 values ('B');
insert into test15 values ('C');
create table test16(y int);
insert into test16 values (1);
insert into test16 values (2);
insert into test16 values (3);
```   
`SELECT * FROM test15, test16;`   
- 내부 결합   
위의 교차결합에서 두개의 테이블을 사용했지만, 여러개의 테이블도 사용가능하다 하지만 테이블 수가 많아지면 집합이 거대해지므로 교차 결합보다는   
내부 결합이 자주 사용된다. 교차결합으로 계산된 곱집합에서 원하는 조합을 검색하는 것을 내부결합이라고 한다.   
```
CREATE TABLE item(itemno char(4) not null, name varchar(30), maker varchar(30), price int, type varchar(30), primary key(itemno));
insert into item values (0001, 'airmax', 'nike', 180000, 'shoes');
insert into item values (0002, 'fury', 'reebok', 230000, 'shoes');
insert into item values (0003, 'oxford shirt', 'polo', 140000, 'cloth');
insert into item values (0004, 'short pants', 'tommy', 120000, 'cloth');
insert into item values (0005, 'black cap', 'nike', 80000, 'cap');
CREATE TABLE stock(itemno char(4), recipedate DATE, quantity int);
insert into stock values (0001, '2020-03-21', 14);
insert into stock values (0002, '2020-02-11', 1);
insert into stock values (0003, '2020-01-23', 5);
insert into stock values (0004, '2020-04-21', 4);
insert into stock values (0005, '2020-04-14', 17);
SELECT * FROM item, stock;
```    
`SELECT * FROM item, stock WHERE item.itemno = stock.itemno;`   
`SELECT item.name, stock.quantity FROM item, stock WHERE item.itemno = stock.itemno AND item.type='shoes';`   
- INNER JOIN으로 내부 결합하기   
최근에는 `INNER JOIN` 키워드를 사용한 결합 방법이 일반적으로 통용된다.   
`SELECT * FROM <테이블명1> INNER JOIN <테이블명2> ON 결합조건`   
`SELECT item.itemno, stock.quantity FROM item INNER JOIN stock ON item.itemno=stock.itemno WHERE item.type ='shoes';`
- 외부결합   
결합 방법은 크게 내부결합과 외부결합의 두 가지로 구분된다.   
외부 결합은 어느 한 쪽에만 존재하는 데이터행을 어떻게 다룰지를 변경할 수 있는 결합 방법이다.   
```
CREATE TABLE item1(itemno char(4) not null, name varchar(30), maker varchar(30), makerno varchar(10), price int, type varchar(30), primary key(itemno));
insert into item1 values (0001, 'airmax', 'nike', 'M001',  180000, 'shoes');
insert into item1 values (0002, 'fury', 'reebok', 'M002', 230000, 'shoes');
insert into item1 values (0003, 'oxford shirt', 'polo', 'M003', 140000, 'cloth');
insert into item1 values (0004, 'short pants', 'tommy', 'M004', 120000, 'cloth');
insert into item1 values (0005, 'black cap', 'nike', 'M001', 80000, 'cap');
insert into item1 values (0009, 'white cap', 'nike', 'M001', 80000, 'cap');
CREATE TABLE stock(itemno char(4), recipedate DATE, quantity int);
insert into stock values (0001, '2020-03-21', 14);
insert into stock values (0002, '2020-02-11', 1);
insert into stock values (0003, '2020-01-23', 5);
insert into stock values (0004, '2020-04-21', 4);
insert into stock values (0005, '2020-04-14', 17);
SELECT * FROM item, stock;
```
`SELECT item1.name, stock1.quantity FROM item1 INNER JOIN stock1 ON item1.itemno = stock1.itemno WHERE item1.type ='cap';`:내부결합에서는 상품코드 0009인 상품이 제외된다.   
(재고수 테이블에는 아직 이 상품에 대한 데이터가 없기 떄문이다.)   
외부결합은 결합하는 테이블 중에 어느 쪽을 기준으로 할지 결정할 수 있다. item1(결합의 왼쪽)을 기준으로 `INNER JOIN` 대신 `LEFT JOIN` 사용한다.   
`SELECT item1.name, stock1.quantity FROM item1 LEFT JOIN stock1 ON item1.itemno = stock1.itemno WHERE item1.type='cap';`   
결합의 오른쪽을 기준으로 하고 싶다면 `RIGHT JOIN` 사용한다.   


