
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
(
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
