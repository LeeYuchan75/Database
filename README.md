## Database

Data : 현실세계에서 수집하는 정보를 의미함

DB(Database) is an organized collection of data

Database management system (DBMS) is the software that interacts with end users, applications, and database itself to capture and analyze data

즉, 데이터베이스 관리 시스템(DBMS)은 최종 사용자, 애플리케이션 및 데이터베이스 자체와 상호 작용하여 데이터를 캡처하고 분석하는 소프트웨어이다

<br/>

## 기업의 DBMS 

DBMS contains information about a particular enterprise

1. A collection of interrelated data

2. A set of programs to access the data

3. An environment that is both convenient and efficient to use

<br/>

**Database systems are used to manage collections of data that are:**

 • Highly valuable

 • Relatively large
 
 • Accessed by multiple users and applications, often at the same time
 
 A modern database system is a complex software system whose task is to manage a large, complex collection of data
 
Databases touch all aspects of our lives (ex: 온라인 쇼핑, 은행 시스템, SNS 등등)

<br/>

![Image](https://github.com/user-attachments/assets/dae00d96-1f27-4f3b-9b5c-e09ab3ec0f49)

<br/>

## 데이터베이스의 목적

**데이터베이스 시스템의 주요 목적은 사용자에게 데이터의 추상적(abstract)인 뷰(View)를 제공하는 것이다**

또한, 파일 시스템의 단점을 극복하기 위함이다

과거에는 데이터베이스 시스템이 존재하지 않았고, 데이터를 저장하려면 단순한 **파일 시스템(File System)** 을 사용해야 했다. 즉, 데이터를 텍스트 파일(.txt), CSV 파일(.csv), 또는 기타 바이너리 파일 형태로 저장하고, 이 파일을 읽고 쓰는 별도의 프로그램을 개발해야 했다.

하지만, 이렇게 파일 시스템을 직접 사용하면 여러 가지 문제점이 발생했다

<br/>

## 1.Data redundancy and inconsistency (데이터 중복과 불일치)

데이터를 여러 개의 파일에 저장하다 보면 중복된 데이터가 생깁니다.
예를 들어, 고객 정보가 "주문 파일"과 "배송 파일" 두 곳에 저장되면, 한 곳에서 정보가 변경되었을 때 다른 곳에는 반영되지 않을 수 있고, 이렇게 되면 데이터 불일치 문제가 발생한다

<br/>

## 2.Difficulty in accessing data (데이터 접근의 어려움)

새로운 작업(예: "5월 매출을 계산하는 기능")을 하려면, 새로운 프로그램을 직접 작성해야 함

즉, 사용자가 새로운 질의(Query)를 할 때마다 프로그래머가 코드를 작성해야 했다

<br/> 

## 3.Data isolation (데이터 고립)

데이터가 여러 개의 파일과 다양한 형식(CSV, JSON, XML 등)으로 저장되면, 특정 데이터를 검색하는 프로그램을 작성하는 것이 어려웠다. 따라서 데이터를 조합하려면 복잡한 프로그램이 필요했음

<br/>

## 4.Integrity problems(무결성 문제)

무결성 제약조건(예: "계좌 잔액은 0 이상이어야 한다")이 데이터베이스 시스템이 아니라 각 프로그램 코드 내부에 포함됨.

이렇게 되면, 새로운 무결성 규칙을 추가하거나 기존 규칙을 변경하는 것이 어려워짐.

예시: "최소 주문 금액을 10,000원에서 15,000원으로 변경해야 한다"면, 관련된 모든 프로그램을 수정해야 함.

<br/>

## 5.Atomicity of updates (원자성)

시스템 오류나 충돌이 발생하면 일부 데이터만 변경된 채 남아, 데이터베이스가 **일관되지 않은 상태(Inconsistent State)** 가 될 수 있음.

즉, 일부 업데이트만 수행된 채 중단되면 데이터 오류가 발생할 가능성이 있다

<br/>

## 6.Concurrent access by multiple users (동시성 문제)

다수의 사용자가 동시에 동일한 데이터를 수정하면 데이터 불일치(Inconsistency) 문제가 발생할 수 있다

<br/>

## 보안 문제

파일 시스템에서는 이런 세밀한 권한 관리가 어렵기 때문에, 보안 문제가 발생할 가능성이 큼.

<br/>

## View of Data

데이터베이스 시스템(Database System)은 **상호 연관된 데이터(interrelated data)와** 이를 **접근하고 수정할 수 있도록 하는 프로그램들의 집합**이다

즉, 데이터베이스 시스템은 데이터를 효율적으로 저장하고 관리하는 소프트웨어 시스템이고 MySQL, PostgreSQL, Oracle DB 등이 이에 해당

주요기능 

1. 데이터를 저장, 검색, 수정, 삭제할 수 있도록 지원

2. 여러 사용자가 동시에 접근할 수 있도록 관리

3.  데이터 일관성 및 보안을 유지

<br/>

**데이터베이스 시스템의 주요 목적은 사용자에게 데이터의 추상적(abstract)인 뷰(View)를 제공하는 것이다**

1. Datac models : 데이터, 데이터 간 관계, 의미, 제약 조건 등을 정의하는 개념적 도구. 쉽게 말해, 데이터를 어떻게 표현할 것인지 설계하는 방법

<br/>

예시: 관계형 데이터 모델(Relational Model)

데이터를 **테이블(Table, 관계형 구조)** 로 표현함. 각 테이블은 **행(Row)과 열(Column)**로 구성되고, SQL을 사용하여 데이터 조작 가능

<br/>

## 예시

![Image](https://github.com/user-attachments/assets/c5963c6d-92a6-4581-bf78-8fbe7f335ace)

<br/>

2. Data Abstraction (데이터 추상화) : 사용자가 데이터의 복잡한 구조를 이해할 필요 없이, 여러 추상화 레벨을 통해 쉽게 사용할 수 있도록 하는 것

<br/>

데이터베이스 시스템이 제공하는 핵심 기능 

<br/>

## 1. Data(데이터)

**데이터를 저장하고 표현하는 방식**

데이터란, 데이터베이스에 저장되는 **실제 값(Value)**을 의미합니다.
예를 들어, 학생 정보를 저장하는 데이터베이스에서는 다음과 같은 데이터를 저장할 수 있습니다.

<br/>

## 2. Data Relationships(데이터 간의 관계)

**데이터 간의 연관성을 정의하는 방식**

현실 세계에서는 데이터가 서로 연결되어 있음.

데이터베이스에서도 이 관계를 모델링하여 표현할 수 있어야 함.

관계형 데이터베이스에서는 테이블 간의 관계(Relationship)를 설정하여 데이터를 효율적으로 연결함.

<br/>

## 3. Data Semantics(데이터 의미)

**데이터가 갖는 의미를 명확히 정의하는 것**

같은 데이터를 저장하더라도 데이터의 의미를 어떻게 해석할 것인지 정의해야 함

데이터가 의미하는 바를 명확히 설명하면, 정확한 검색과 처리가 가능

<br/>

## 4.Data Constraints(데이터 제약 조건)

**데이터의 무결성을 유지하기 위해 설정하는 규칙** (무결성 : 데이터의 정확성과 일관성을 유지하는 것)

데이터의 **일관성(Consistency)** 을 유지하기 위해 특정한 규칙(Constraints)을 설정함.

잘못된 데이터 입력을 방지하여 데이터베이스의 신뢰성을 높임.









