## Relational Data Model

Relation Data model : 데이터를 행(Row)과 열(Column)로 구성된 테이블의 형태로 표현하는 데이터 모델

![image](https://github.com/user-attachments/assets/58bc7aab-b348-49a4-b804-598adf2c2da8)

왼쪽에 있는 표를 오른쪽과 같이 relation model로 데이터베이스 구축 

<br/>

전체적인 표 : tabel 

튜플 (행): 열(column)에 해당하는 값들이 모여 정보를 나타내는 집합

속성 (열): 각 열이 의미하는 것 (ex: 이름,ID)

하나의 축에는 하나의 attribute가 들어가야 하고, 데이터의 순서는 상관 없음 

속성이 가질 수 있는 값을 domains of attribute 라고 함 

**relational database** : 위와 같은 테이블 집합

![image](https://github.com/user-attachments/assets/9336f838-34f6-49e7-bb7f-edc1b85b3472)

<br/>

## Database Schema and instance

1. 데이터베이스 스키마 (Schema) : 데이터베이스의 구조나 설계도. 테이블, 칼럼, 관계, 제약 조건 등이 포함됨

2. 데이터베이스 인스턴스 (Instance) : 데이터베이스의 실제 데이터 상태. 특정 시점에 데이터베이스가 어떻게 구성되어 있는지를 나타냄

<br/>

## The purpose of schema design

스키마 설계의 목적 : 데이터베이스와 각 관계를 설계하여 서로 다른 관계의 튜플들을 연결

<br/>

## Key

1. Super Key: 모든 행을 유일하게 식별할 수 있는 속성(집합)

2. Candidate Key: 슈퍼키 중에서 최소성을 만족하는 키

3. Primary Key: 후보키 중에서 하나를 선택한 키

<br/>

## 스키마 다이어그램 (Schema Diagram)

Schema Diagram : 데이터베이스의 스키마(구조)를 그림으로 표현한 것

<br/>

## Relational Query Language

Relational Query Language : 관계형 데이터베이스에서 테이블을 조작하고 결과를 테이블 형태로 반환하는 언어














































































































































