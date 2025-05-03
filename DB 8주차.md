## 데이터베이스 설계 과정

데이트비이스 설계 과정은 다음과 같이 진행된다 

1. Initial Phase : **사용자 요구를 이해**하고 필요한 데이터를 규명함

2. Second Phase :  요구사항을 **관계형 데이터 모델**로 구체화

3. Final Phase : 논리적/물리적 구현을 위한 **데이터베이스** 구체화

이것에 대해 자세히 알아보자 

<br/>

## initial Phase 

쇼핑몰 웹사이트에서 사용하는 것으로 예를 들겠다 

![image](https://github.com/user-attachments/assets/488da209-d8b1-4275-8bbd-1672f6f35b7c)

초기 단계의 **핵심 목적**은 **사용자 요구를 이해**하고 필요한 데이터를 규명하는 것이다 

즉, 아래와 같이 prospective database users(예비 사용자)의 **데이터 요구를 완전히 이해하는 것**이 목적이다

- 고객 정보 필요 (이름, 이메일, 전화번호 등)

- 상품 정보 관리 (상품명, 가격, 재고 등)

- 주문 내역 저장

- 장바구니 기능

- 리뷰/평가 기능

- 배송 상태 추적

**핵심 포인트 : 무엇을 저장해야 하는가?** 에 대한 **사용자 관점의 요구를 명확히** 하는 단계이다 

<br/>

## Second Phase

두번째 단계의 핵심 목적은 요구사항을 **관계형 데이터 모델로 구체화**하는 것이다

데이터 모델로 관계형 모델(Relational Model)을 사용하고 

선택한 데이터 모델의 개념을 적용해야한다 

- 고객(Customer)

- 상품(Product)

- 주문(Order)

- 장바구니(Cart)

- 리뷰(Review)

이후 요구사항을 데이터베이스의 개념적 스키마로 변환을 해야한다

여기서 **개념적 스키마**란 사용자 요구를 기반으로 어떤 데이터를 저장하고, 엔터티(테이블) 간에 어떤 관계가 있는지를 표현한 설계도를 의미한다

- 고객 1명은 여러 주문을 할 수 있음 (1:N)

- 주문 1건은 여러 상품을 포함할 수 있음 (M:N → 주문상세 테이블 필요)

이 단계의 핵심 포인트는 개념적 설계로 옮기기 위한 **구조화된 모델 설계 및 관계 정의**이다 

<br/>

## Final Phase

마지막 단계에서는 앞에서 만든 개념적 모델을 **실제 데이터베이스 설계와 성능에 맞게 구체화**하는 것이다

이 과정은 크게 **Logical Design**과 **Physical Design**으로 분류되고, Logical Design는 **Business decision**과 **Computer Science decision**으로 분리가 된다 

<bt/>

**1. Logical Design**

이 단계에서는 좋은 관계 스키마의 집합을 찾아야 한다. 즉, 어떤 테이블(릴레이션)을 만들고, 어떤 속성을 포함할지 결정해야 적절하게 결정해야 한다 

- **Business decision** : 데이터베이스에 어떤 속성을 저장할 것인가? (고객 테이블에 이름, 이메일, 전화번호, 배송 주소를 저장할 것인가?)

- **Computer Science decision** : 어떤 릴레이션(테이블)을 만들고, 어떤 속성을 어떤 테이블에 나눌 것인가? (ex: 고객(Customer), 상품(Product), 주문(Order), 주문 상세(OrderItem) 테이블을 따로 만들 것인가?)

<br/>

**2. Physical Design**

Physical Designd은 데이터베이스의 물리적 배치를 결정하는 것이다 

쉽게 말해 어디에 저장을 할 것인지를 결정

ex: 고객 테이블에 인덱스를 설정하여 빠른 검색이 가능하도록 구현

<br/>

## E-R model 

ER 데이터 모델은 데이터베이스 설계를 용이하게 하기 위해 개발됨 

기업 전체의 데이터 요구를 반영하는 데이터베이스인 **enterprise schema(기업 스키마)** 를 정의할 수 있도록 해준다

ER 모델은 세 가지 기본 개념을 사용한다

- **entity sets** (엔터티 집합)

- **relationship sets** (관계 집합)

- **attributes** (속성)

<br/>

ER 모델은 **ER 다이어그램**이라는 시각적 표현을 가지고 있고

이 다이어그램은 데이터베이스의 **전체 논리 구조를 생생하게 표현**할 수 있다

그럼 이제 entitiy set, relationship set, attributes를 순차적으로 알아보자 

<br/>

## Entitiy set

**Entity** : 실제로 존재하며 **다른 객체와 구분되는 것** (ex: 특정 사람, 회사, 사건, 식물 등)

**Entity set** : 동일한 속성을 공유하는 **객체들의 집합** (ex: 모든 사람들의 집합, 모든 회사들의 집합 등)

이해를 돕기 위해 아래 표를 제시하였다 

![image](https://github.com/user-attachments/assets/78ac35f4-2989-446c-bbf1-00f5063d6184)

위 표처럼 Entity는 현실 세계의 관점에서 생각한 것이고 우리는 이러한 현실 세계를 컴퓨터로 구현을 해야하는 역할을 한다 

<br/>

내용을 이어서 설명하자면 

하나의 엔터티는 여러 개의 속성으로 표현이 된다. 여기서 속성(attribute)이란 그 엔터티의 특징 설명하는 역할을 하고, 우리가 ralation table에서 사용한 attribute와 동일한개념이다 

ex: instructor = (ID, name, salary), course = (course_id, title, credits)


또한, 속성들 중 일부는 **기본 키(primary key)** 가 된다. 기본 키는 각 엔터티를 고유하게 식별한다 

<br/>

**예시**

![IMG_3164](https://github.com/user-attachments/assets/1aa37c19-c05d-4bbc-9acc-5464f686eea2)

<br/>

## Entity sets & ER Diagram

아래는 Entity set을 ER Diagram으로 표현하는 방식이다 

![image](https://github.com/user-attachments/assets/9da7189d-6221-442b-b415-1d9708ad2774)

- 파란색 직사각형은 엔터티 집합을 의미한다 (ex: instructor, student)

- 속성들은 직사각형 안에 나열된다 (ex: name, salary 등)

- 밑줄은 기본 키(primary key) 속성을 나타낸다 (ex: ID에 밑줄 → 기본 키)

<br/>

## Relationship Sets

**Relationship sets**은 서로 다른 **Entity 사이의 관계** 와 그것을 모아 놓은 **관계 집합** 을 설명

<br/>

**예시**

![image](https://github.com/user-attachments/assets/69791b46-1ef2-4efb-b3fe-891232de3d9f)

student Entity와 instructor entity가 서로 advisor(지도 교수)라는 관계로 연결됨 (Peltier 학생의 지도교수는 Einstein이다)

수학적으로 표현하면 다음과 같다 (44553,22222) ∈ advisor

우리가 앞에서 table를 구현한 것을 예로 들면, student와 course table이 있을 때, 두 table를 task라는 table를 이용하여 서로 연결하였다. 

이때 student와 course table은 Entity이고 task table은 relationship set의 역할을 한다


























































