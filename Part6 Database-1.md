# Database review

#### 데이터베이스 생성
#### CREATE DATABASE [데이터베이스 이름];
##
#### 데이터베이스 조회
#### SHOW DATABASES;
##
#### 데이터베이스 선택
#### USE [데이터베이스 이름];
##
#### 데이터베이스 삭제
#### DROP DATABASE [데이터베이스 이름];
##
#### 테이블 조회
#### USE [테이블 이름];
##
#### 테이블 생성
#### CREATE TABLE [테이블 이름] (
####    -------
####    -------
####    -------
#### );   
##
#### 테이블 삭제
#### DROP TABLE [테이블 이름];
##
#### 테이블 정보 확인
#### DESC [테이블 이름];
##
#### 테이블 정보 수정
##### 테이블 새로운 컬럼 추가 
##### ALTER TABLE [테이블 이름] ADD COLUMN [컬럼 이름][컬럼 타입][컬럽 옵션];
##### 테이블 기존 컬럼 타입 변경
##### ALTER TABLE [테이블 이름] MODIFY COLUMN [컬럼 이름][변경할 컬럼 타입][컬럼 옵션];
##### 테이블 기존 컬럼 삭제
##### ALTER TABLE [테이블 이름] DROP COLUMN [컬럼 이름]; --> 삭제시 복구 불가
## 까먹지 말것
#### PRIMARY KEY는 하나의 테이블에서 여러개 불가
#### DATETIME : YYYY-MM-DD HH:MM:SS (시간O)
#### DATE : YYYY-MM-DD (시간X)
