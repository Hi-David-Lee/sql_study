
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
6. TABLE 데이터 입력   
`INSERT INTO <TABLE 명> (열 이름1, 열 이름2, 열 이름3, ...) VALUES ('값1', '값2', '값3',...);`   
`INSERT INTO test (name, birthday, address) VALUES ('david', '1991-01-06', 'SungNam, Korea');` 
7. DATABASED 데이터 읽기   
`SELECT * FROM <TABLE 명>;`   
'SELECT * FROM test;`   
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






