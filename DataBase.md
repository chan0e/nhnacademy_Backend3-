###### 실습 DB는 MySQL로 진행됨
###### 사진 출처는 NHNacademy
### 데이터베이스 개요

+ 데이터(Data)

  현실 세계로부터 단순한 관찰이나 측정을 통해서 수집된 사실이나 값
  
+ 정보(Information)

  어떤 상황에 대한 적절한 의사 결정을 할 수 있게하는 지식으로서 유효한 데이터의 해석 또는 데이터간의 관계
  
+ 정보는 데이터를 처리해서 얻어진 결과

### 데이터 베이스
+ 같은 데이터가 다른 목적을 가진 여러 응용에 중복되어 사용될 수 있다는 공용 개념의 기초
  - 통합된 데이터(Integerated Data)
  - 저장된 데이터(Stored Data)
  - 운영 데이터(Operational Data)
  - 공용 데이터(Shared Data)


+ 통합 저장된 운영 데이터로서의 특징
  - 실시간 접근성(Real-time Accessibility)
  - 지속적인 변화(Continuous Evolution)
  - 동시 사용(Concurrency Sharing)
  - 내용 참조(Content Reference)


### 데이터베이스 관리 시스템(DBMS, Database Management System)

+ 데이터의 방대한 집합체를 유지 관리하고 이용하는데 도움을 주도록 설계된 소프트웨어
+ 데이터의 종속성과 중복성의 문제를 해결하기 위해 제안된 시스템 

![image](https://user-images.githubusercontent.com/94053008/226253719-47b1568e-ca6b-4189-8ec3-572002e4e9ee.png)


### 데이터베이스 관리 시스템의 기능

+ 데이터 정의 기능
  - 데이터 모델과 데이터베이스를 물리적 저장 장치에 저장하는데 필요한 명세 포함
  - 논리적 구조와 물리적 구조의 매핑을 명세
  
+ 데이터 조작 기능
  - 사용자와 데이터베이스 사이의 인터페이스를 위한 수단 제공
  
+ 데이터 제어 기능
  - 데이터의 갱신, 삽입, 삭제 작업이 정확히 실행되며, 무결성 제공
  - 보안과 권한 검사
  - 동시 사용자에 대한 병행성 제어


#### 데이터 모델

![image](https://user-images.githubusercontent.com/94053008/226254629-d09cbdc5-f07d-4f80-be5d-ec830b26d333.png)

+ 데이터 또는 정보를 설명하기 위한 표기법
  - 데이터의 구조(Structure of the Data)
  - 데이터에 대한 작업(Operations on the Data)
  - 데이터에 대한 제약 조건(Constraints on the Data)

+ 주요 데이터 모델
  - 관계 데이터 모델(Relational Data Model)
  - 반정형 데이터 모델(Semi-Structured-data Model)
 
 
 
 #### 트랜잭션(ACID)
 
 + Atmoicity
   - 트랜잭션과 관련된 작업들이 부분적으로 실행되다가 중되지 않음을 보장
 + Consistency
   - 실행을 완료하면 언제나 일관성 있는 데이터베이스 상태로 유지됨을 보장
 + Isoloation
   - 트랜잭션 수행 시 다른 트랜잭션의 연산작업이 끼어들지 못하도록 보장
 + Durability
   - 성공적으로 수행된 트랜잭션은 영구적으로 데이터베이스에 지속됨을 보장

### 교차수행에 의한 일부 이상
+ 기록-판독 충독(WR Conflict)
+ 판독-기록 충돌(RW Conflict)
+ 기록-기록 충돌(WW Conflict)

### Lock
+ 데이터의 일관성과 무결성을 보장하기 위해 사용되는 중요한 개념 중 하나
+ 다수의 사용자가 동시에 데이터에 접근할 때 일어날수 있는 데이터의 불일치를 막기위함

+ Lock Mode
  - Shared Lock Mode
     + 다른 트랜잭션이 읽기 작업을 할 수 있도록 데이터를 읽을수 있지만, 쓰기 작업을 하려면 락을 획득해야 하는 모드
  - Exclusive Lock Mode
     + 해당 트랜잭션이 사용중인 데이터를 다른 트랜잭션이 읽거나 쓰지 못하도록 배타적으로 락을 거는 모드
  -  Strict 2 Phase Lock
     + 두 단계의 락 방식으로 구성
     + 첫번째 단계 : 트랜잭션은 데이터를 읽이 위해 공유 락을 요청
     + 두번째 단계 : 데이터를 수정하기 위해 배타 락을 요청
     + 다수의 트랜잭션이 동시에 같은 데이터에 접근하는 경우 발생할 수 있는 갱신 분실, 모순성 등의 문제를 방지

###### 배타적(exclusive) : 어떤 리소스를 하나의 프로세스나 스레드만 사용할 수 있도록 하는것을 의미

### 잠금 관리
+ DBMS는 Lock Manager를 제공
+ 잠금 요청과 잠금 해제 요청 구현

### Deadlock
+ 두 트랜잭션이 잠금 해제를 기다리는 관계에 사이클이 생기는 경우
![image](https://user-images.githubusercontent.com/94053008/235834102-5e11d157-6013-4829-bf00-655cbb7c4cac.png)

+ 논리적으로 교착상태를 막을 수 있는 방법은 없으나 예방은 가능 ex) 프로세스의 시작을 막는다거나......




### 무결성 제약조건 개요
+ 저장된 정보의 품질에 따라 데이터베이스의 품질이 결정됨

1. 개체무결성
   : 각 릴레이션의 기본키를 구성하는 속성은 NULL 값이나 중복된 값을 가질수 없음.

3. 참조무결성
   : 외래키 값은 NULL이거나 참조하는 릴레이션의 기본키 값과 동일해야 한다.
   
5. 도메인무결성
   : 속성들의 값은 정의된 도메인에 속한 값이어야 한다.


#### KEY의 개념

KEY는 데이터베이스에서 조건에 만족하는. 튜플을 찾거나 순서대로 정렬할때 다른 튜플들과 구별할 수 있는 기준이 되는 속성

+ Candidate Key
  - 유일하게 식별할 수 있는 속성들의 부분집합
  - 모든 릴레이션은 반드시 하나 이상의 후보키를 가져야함
  - 유일성과 최소성을 만족


+ Primary Key
  - 후보키 중에서 선택한 주키(Main Key)
  - 특정 튜플을 유일하게 구별하는 속성
  - NULL 값을 가질수 없고 중복된 값을 저장할 수 없음 (개체 무결성 조건)


+ Alternate Key
  - 후보키가 둘 이상일 때 기본키를 제외한 나머지 후보키들


+ Super Key
  - 한 릴레이션에 존재하는 속성들의 집합으로 구성된 키
  - 유일성은 만족하지만 최소성은 만족하지 못함

+ Foreign Key
  - 관계를 맺고 있는 두개의 릴레이션 R1, R2에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성
  - 참조되는 릴레이션의 기본키와 대응되어 참조관계를 표현하는데 중요한 키
  - 외래키로 지정되면 참조 테이블의 기본키에 없는 값은 입력할 수 없음 (참조 무결성 조건)
   
   ***
   
   ### 관계 대수
   
   - 어떻게 질의를 해석하는가에 대한 언급하는 절차적 언어

   #### 연산자
   
   
   ![image](https://user-images.githubusercontent.com/94053008/226772647-c2362fe2-7400-47c1-8463-75085ce3188e.png)
    
    (출처 - https://inpa.tistory.com/entry/DB-📚-관계-대수-관계-해석-SQL-🕵%EF%B8%8F-정리)
    
  
   + Selection : 테이블에서 데이터를 가져옴
      - 원하는 데이터를 수평적으로 도출
  
   + Projection : 테이블에서 특정한 조건을 준 데이터만 출력
      - 원하는 데이터를 수직적으로 도출함
      - 한 릴레이션의 애트리뷰트들의 부분 집합을 구함
      - 셀렉션의 결과 릴레이션에는 중복 튜플이 존재불가, 프로젝션 연산의 결과에서는 존재할 수 있음


   + Union : 중복된걸 제외하고 테이블의 합
      - 결과 릴레이션에서 중복된 튜플들은 제외됨
      - 두 테이블에 튜플의 갯수가 다르거나 도메인이 다르면 안됨


   + Intersection : 중복된것을 보여주는 테이블
      
   + Difference : A - B를 한 결과 테이블
   + Cartesian Product : A 테이블과 B 테이블의 튜플수를 곱한 테이블의 결과
   + Join : 두 테이블들과의 결합 (주키 테이블에서 외래키 테이블로 Join하는것이 속도가 빠름)
     - Theta Join, Equi Join
        - {=, <>, <=, <, >=, >} 중의 하나
        - 동등 조인은 세타 조인 중에서 비교 연산자가 = 인 조인

     - Natural Join
       
     - Outer Join
     - Semi Join
   + Division : 두 테이블과의 분할
 
 
 
 ***
 
 ### SQL 구성
 
 + 데이터 조작어(Data Manipulation Language, DML)
    - 관계 대수와 튜플 관계 해석에 기반한 질의 언어를 포함
    - DB에 튜플을 삽입, 삭제하며 수정하는 명령어를 포함
    - Select, Insert, Updata, Delete
    
  


    
 + 데이터 정의어(Data Definition Language, DDL)
    - 릴레이션 스키마를 정의하고, 삭제하고 수정하는 명령어들을 제공
    - DB에 저장될 데이터가 만족해야 할 무결정 제약조건을 명시하는 명령어와 릴레이션과 뷰 등에 접근하는 권한을 
      명시하는 명령을 포함
    - Create, Alter, Drop, Rename, Truncate


    + 생성
      - CREATE TABLE {Table Name} (
        [Column Name] [Data Type] {NULL | NOT NULL} {Column Option} {Constraint List} [Constraint definition]
        )
        
    + 수정
      - ALTER TABLE [TableName]
        {ALTER COLUMN} [COLUMN NAME] {Column Option} {ADD} (Column | Constraints} 
        {ADD Option} {DROP} (Column | Constraints} {DROP Option}
        
    + 삭제
      - DROP TABLE [TableName]

 + 데이터 제어어(Data Control Language, DCL)
    - 테이블이나 뷰 등의 데이터에 대한 사용자의 접근을 제어하는 명령어를 포함
    - Grant, Revoke, Deny
 
 
 
 ***
 My sql에 기본 DBEngine은 InnoDB, 관리자가 엔진을 다르게 바꿔주면 물리적으로 봤을때 데이터들은 각 다른 곳에서 존재하므로 키 제약조건이나 원할하게 명령어를 진행할려면
 엔진을 같게 맞춰야함
 
 
 
## 데이터베이스 설계
+ 데이터베이스의 구조와 관계를 정의하고, 데이터베이스의 요구사항을 충족시키기위해 데이터를 구성하는 프로세스
+ DB 개발과정에서 가장 중요한 단계 중 하나

## ERD(Entity-Relationship Diagram)
+ 데이터 베이스 설계를 시각화하는 도구중 하나
+ 엔티티와 엔티티 간의 관계를 표시하여 데이터베이스의 구조와 관계를 시각적으로 표현

### ERD 일반적인 절차
1. 요구사항 수집: 데이터베이스 설계를 시작하기 전에, 시스템에 필요한 데이터 요구사항을 수집 이를 통해 DB의 기능과 제약사항을 정의할 수 있음
2. 개념적 설계: 요구사항을 바탕으로 엔티티, 속성, 관계를 정의하고 이를 개념적 모델로 표현
3. 논리적 설계: 개념적 모델을 기반으로, 엔티티와 관계를 더 상세하게 정의 이를통해 DB의 정규화와 익데스 등의 요소를 결정
4. 물리적 설계: 논리적 모델을 물리적으로 구현하기위해 테이블, 필드, 제약조건 등의 구체적인 정보를 추가
5. 구현: 데이터베이스를 구현하고, 초기 데이터를 입력
6. 유지보수

### ERD 표기법
+ Entity: 사각형으로 표현
+ Attribute: 타원형으로 표현
+ Relationship: 엔티티간의 속성을 표시. 마름모로 표현
  
  
### 식별관계 와 비식별관계
+ 식별관계
  - 부모 테이블(=참조되는 테이블)의 기본키를 자식테이블(=참조하는 테이블)의 기본키로 이용하는 방법

+ 비식별관계
  - 부모 테이블(=참조되는 테이블)의 기본키를 자식테이블(=참조하는 테이블)의 외래키로 이용하는 방법

+ 차이점
  - 식별관계를 사용할 경우 반드시 부모테이블에 데이터가 존재해야만 자식테이블에 데이터를 추가 할 수 있음
  - 비식별관계는 부모 데이터가 없어도 자식 테이블에서 데이터를 추가 할 수 있음
  - 다만 비식별관계는 데이터 정합성을 보장하지 않지만 구조 변경이 자유롭고, 식별관계는 구조 변경이 자유롭지 못하지만 데이터 정합성을 보장한다.
  ###### 데이터 정합성: 데이터의 유효성, 일관성, 무결성, 정확성을 보장하는 것

  
## 정규화(Denormalization)
+ 데이터베이스 설계과정에서 중복을 최소화하고 데이터의 일관성과 무결성을 유지하기 위해 릴레이션을 분해하는 과정
+ DB의 성능과 유지보수를 향상시키는데 도움이 됨

### 1차 정규화
+ 각 속성이 원자적(Atomic)
+ 즉, 하나의 속성은 더 이상 분해할 수 없는 단위여야 함
<img width="669" alt="image" src="https://user-images.githubusercontent.com/94053008/234485723-699aa44d-8302-47ff-8788-ad1be4919707.png">

+ 주문 상품이 column으로 중복되어 나타나고 있음 -> 1차 정규화

#### 고객 정보 테이블
<img width="667" alt="image" src="https://user-images.githubusercontent.com/94053008/234485929-d7bc4621-5fb4-4444-9936-0aeff99ff193.png">

#### 주문 상품 정보 테이블
<img width="674" alt="image" src="https://user-images.githubusercontent.com/94053008/234486018-18ba2afc-d6e4-4824-a099-b33e4e5a8ad8.png">

### 2차 정규화
+ 1차 정규화를 완료한 상태에서 부분적 종속 관계를 제거하는 과정
+ 즉, 모든 비주요 속성이 주요속성에 대해서만 종속되도록 테이블을 분해함

> 학생 성적 데이터

<img width="673" alt="image" src="https://user-images.githubusercontent.com/94053008/234487311-4d5d14eb-bbdc-444a-8438-ef91850c0a5c.png">

+ 학번이 주요 속성, 나머지 세 가지 속성은 학번에 대해서 부분적으로 종속되어 있음

#### 학생 정보테이블(학번,학과)
<img width="676" alt="image" src="https://user-images.githubusercontent.com/94053008/234487666-f283601f-57a9-4ebc-ae28-c0fdbb6b675e.png">


#### 성적 정보 테이블(학번,과목,성적)

<img width="668" alt="image" src="https://user-images.githubusercontent.com/94053008/234487883-79c0ac35-8a39-432e-a5c2-b0aadbba5bf7.png">

### 3차 정규화
+ 테이블에서 이행적 종속을 제거하는데 초점을 둔 정규화
+ 3차 정규화를 통해 테이블이 모든 행에 대해 키에 의존하지 않도록 만들어짐

#### 상품 테이블 

<img width="670" alt="image" src="https://user-images.githubusercontent.com/94053008/234492229-912f501a-2926-42c7-a6fb-592a2a87e656.png">

+ 2차 정규화까지 적용되어 있음
+ 모든 컬럼이 후보키에 포함되거나 후보키에 종속적인 컬럼으로만 구성되어 있음


#### 상품 테이블

<img width="655" alt="image" src="https://user-images.githubusercontent.com/94053008/234492713-f8963a0b-4920-4d12-8751-eee1c3a898d1.png">

#### 제조사 테이블

<img width="664" alt="image" src="https://user-images.githubusercontent.com/94053008/234492767-c7051251-e802-4654-9990-7500f4a542e7.png">


#### 제조국가 테이블
<img width="667" alt="image" src="https://user-images.githubusercontent.com/94053008/234492826-293c2bb4-9f71-4c96-97e4-c441bc3b702b.png">


### BNCF(Boyce-Codd Normal Form)
+ 모든 결정자는 후보키인 테이블 형태
+ 결정자가 후보키의 일부가 아닌경우 이를 분해하여 새로운 릴레이션을 생성해야 함
+ 모든 함수적 종속을 만족하면서 이상 현상을 제거

#### 상품 테이블

<img width="673" alt="image" src="https://user-images.githubusercontent.com/94053008/234494344-17510c0e-f10a-4357-b078-c2144202ee07.png">

+ 제조사 ID는 후보키이지만 상품명에 따라서도 가격이 결정될 수 있음
+ 상품명은 제조사 ID에 종속적이라는 문제점이 있어 이를 해결하기 위해 제조사 정보를 별도의 테이블로 분리

#### 제조사 테이블


<img width="668" alt="image" src="https://user-images.githubusercontent.com/94053008/234494815-c801566f-3372-437f-baec-408ef73b01b7.png">









